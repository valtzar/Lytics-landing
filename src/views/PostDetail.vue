<template>
  <section class="post-detail">
    <div class="container">
      <!-- Loading State -->
      <div v-if="loading" class="loading-state">
        <p>⏳ Cargando artículo...</p>
      </div>

      <!-- Error State -->
      <div v-else-if="error" class="error-state">
        <p>⚠️ No pudimos cargar el artículo.</p>
        <p class="error-detail">{{ error }}</p>
        <button @click="$router.back()" class="btn btn-primary">← Volver al Blog</button>
      </div>

      <!-- Post Content -->
      <div v-else-if="post" class="post-wrapper">
        <!-- Back Button -->
        <button @click="$router.back()" class="back-link">← Volver al Blog</button>

        <!-- Post Header -->
        <div class="post-header">
          <h1 class="post-title">{{ post.Titulo }}</h1>
          <div v-if="post.createdAt" class="post-meta">
            📅 {{ formatDate(post.createdAt) }}
          </div>
        </div>

        <!-- Post Image -->
        <div v-if="post.Portada && post.Portada.url" class="post-featured-image">
          <img :src="getImageUrl(post.Portada.url)" :alt="post.Titulo" />
        </div>

        <!-- Post Body -->
        <div class="post-body">
          <div v-if="post.Contenido" class="post-content">
            <RichTextRenderer :content="post.Contenido" />
          </div>
          <p v-else class="no-content">No hay contenido disponible para este artículo.</p>
        </div>

        <!-- Back Button (Bottom) -->
        <div class="post-footer">
          <button @click="$router.back()" class="btn btn-secondary">← Volver al Blog</button>
        </div>
      </div>

      <!-- Not Found -->
      <div v-else class="not-found">
        <p>Artículo no encontrado</p>
        <router-link to="/" class="btn btn-primary">Volver al Blog</router-link>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useRoute } from 'vue-router'
import RichTextRenderer from '../components/RichTextRenderer.vue'

const route = useRoute()
const post = ref(null)
const loading = ref(false)
const error = ref(null)

const getImageUrl = (imagePath) => {
  if (imagePath.startsWith('http')) {
    return imagePath
  }
  return `http://localhost:1337${imagePath}`
}

const formatDate = (dateString) => {
  const date = new Date(dateString)
  return new Intl.DateTimeFormat('es-CL', {
    year: 'numeric',
    month: 'long',
    day: 'numeric'
  }).format(date)
}

const normalizePost = (rawPost) => {
  // Si Strapi v5 devuelve estructura con 'attributes'
  if (rawPost.attributes) {
    return {
      id: rawPost.id,
      ...rawPost.attributes
    }
  }
  // Si ya viene normalizado
  return rawPost
}

const fetchPost = async () => {
  loading.value = true
  error.value = null

  try {
    const documentId = route.params.id
    const response = await fetch(`http://localhost:1337/api/posts/${documentId}?populate=*`)

    if (!response.ok) {
      throw new Error(`Error ${response.status}: No se encontró el artículo`)
    }

    const data = await response.json()
    post.value = normalizePost(data.data)

  } catch (err) {
    console.error('Error fetching post:', err)
    error.value = err.message || 'Error desconocido al cargar el artículo'
  } finally {
    loading.value = false
  }
}

onMounted(() => {
  fetchPost()
})
</script>

<style scoped>
.post-detail {
  padding: var(--spacing-3xl) 0;
  background-color: var(--color-white);
  min-height: calc(100vh - 200px);
}

.container {
  max-width: 800px;
  margin: 0 auto;
  padding: 0 var(--spacing-md);
}

/* Back Link */
.back-link {
  display: inline-flex;
  align-items: center;
  gap: var(--spacing-sm);
  font-size: var(--font-size-base);
  font-weight: var(--font-weight-bold);
  color: var(--color-primary);
  text-decoration: none;
  margin-bottom: var(--spacing-2xl);
  transition: all var(--transition-fast);
  background: none;
  border: none;
  cursor: pointer;
  padding: 0;
  font: inherit;
}

.back-link:hover {
  color: var(--color-primary-dark);
  gap: var(--spacing-md);
}

/* Post Header */
.post-header {
  margin-bottom: var(--spacing-2xl);
  padding-bottom: var(--spacing-2xl);
  border-bottom: 2px solid var(--color-gray-200);
}

.post-title {
  font-size: var(--font-size-5xl);
  line-height: var(--line-height-tight);
  color: var(--color-black);
  font-weight: var(--font-weight-bold);
  margin: 0 0 var(--spacing-md) 0;
}

.post-meta {
  font-size: var(--font-size-base);
  color: var(--color-gray-600);
}

/* Featured Image */
.post-featured-image {
  width: 100%;
  max-height: 500px;
  margin: var(--spacing-2xl) 0;
  border-radius: var(--border-radius-lg);
  overflow: hidden;
  box-shadow: var(--shadow-lg);
}

.post-featured-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

/* Post Body */
.post-body {
  margin: var(--spacing-2xl) 0;
  font-size: var(--font-size-lg);
  line-height: var(--line-height-relaxed);
  color: var(--color-gray-700);
}

.post-content {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-lg);
}

.no-content {
  text-align: center;
  padding: var(--spacing-2xl);
  background-color: var(--color-gray-50);
  border-radius: var(--border-radius-lg);
  color: var(--color-gray-600);
}

/* Post Footer */
.post-footer {
  margin-top: var(--spacing-3xl);
  padding-top: var(--spacing-2xl);
  border-top: 2px solid var(--color-gray-200);
  text-align: center;
}

/* States */
.loading-state,
.error-state,
.not-found {
  text-align: center;
  padding: var(--spacing-3xl) var(--spacing-xl);
  background-color: var(--color-gray-50);
  border-radius: var(--border-radius-lg);
  margin: var(--spacing-2xl) 0;
}

.loading-state p,
.error-state p,
.not-found p {
  font-size: var(--font-size-xl);
  color: var(--color-gray-600);
  margin: 0 0 var(--spacing-lg) 0;
}

.error-detail {
  font-size: var(--font-size-base);
  color: var(--color-gray-500);
}

@media (max-width: 768px) {
  .post-detail {
    padding: var(--spacing-2xl) 0;
  }

  .post-title {
    font-size: var(--font-size-3xl);
  }

  .post-featured-image {
    max-height: 300px;
  }

  .post-body {
    font-size: var(--font-size-base);
  }
}
</style>
