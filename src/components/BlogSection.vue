<template>
  <section class="blog-section">
    <div class="container">
      <div class="blog-header">
        <h2>Blog & Recursos</h2>
        <p class="blog-subtitle">Insights, casos de estudio y mejores prácticas en People Analytics</p>
      </div>

      <!-- Loading State -->
      <div v-if="loading" class="loading-state">
        <p>⏳ Cargando posts...</p>
      </div>

      <!-- Error State -->
      <div v-else-if="error" class="error-state">
        <p>⚠️ No pudimos cargar los posts. Por favor intenta más tarde.</p>
        <p class="error-detail">{{ error }}</p>
      </div>

      <!-- Posts Grid -->
      <div v-else-if="posts.length > 0" class="posts-grid">
        <article v-for="post in posts" :key="post.id" class="post-card">
          <!-- Post Image -->
          <div class="post-image" v-if="post.Portada && post.Portada.url">
            <img :src="getImageUrl(post.Portada.url)" :alt="post.Titulo" />
          </div>
          <div v-else class="post-image placeholder">
            <span>📰</span>
          </div>

          <!-- Post Content -->
          <div class="post-content">
            <h3 class="post-title">{{ post.Titulo }}</h3>
            
            <p class="post-excerpt">
              {{ getFirstParagraph(post.Contenido) }}
            </p>

            <router-link :to="`/post/${post.documentId}`" class="post-link">
              Leer más
              <span class="arrow">→</span>
            </router-link>
          </div>
        </article>
      </div>

      <!-- Empty State -->
      <div v-else class="empty-state">
        <p>No hay posts disponibles en este momento.</p>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'BlogSection',
  data() {
    return {
      posts: [],
      loading: false,
      error: null
    }
  },
  mounted() {
    this.fetchPosts()
  },
  methods: {
    async fetchPosts() {
      this.loading = true
      this.error = null
      
      try {
        const response = await fetch('http://localhost:1337/api/posts?populate=*')
        
        if (!response.ok) {
          throw new Error(`Error ${response.status}: ${response.statusText}`)
        }
        
        const data = await response.json()
        this.posts = (data.data || []).map(post => this.normalizePost(post))
        
      } catch (err) {
        console.error('Error fetching posts:', err)
        this.error = err.message || 'Error desconocido al cargar los posts'
      } finally {
        this.loading = false
      }
    },

    getImageUrl(imagePath) {
      // Si ya tiene la URL completa, retornarla tal cual
      if (imagePath.startsWith('http')) {
        return imagePath
      }
      // Concatenar base URL + path relativo
      return `http://localhost:1337${imagePath}`
    },

    getFirstParagraph(contenido) {
      // Si no hay contenido, retornar texto vacío
      if (!contenido) return 'Sin descripción disponible.'
      
      // Si contenido es un string, retornar el primero 150 caracteres
      if (typeof contenido === 'string') {
        return contenido.substring(0, 150) + (contenido.length > 150 ? '...' : '')
      }
      
      // Si contenido es un array (bloques de Strapi)
      if (Array.isArray(contenido)) {
        for (const block of contenido) {
          // Buscar bloques de párrafo
          if (block.type === 'paragraph') {
            const text = block.children?.map(child => child.text).join('') || ''
            if (text.trim().length > 0) {
              return text.substring(0, 150) + (text.length > 150 ? '...' : '')
            }
          }
        }
      }
      
      // Si contenido es un objeto con children (otra estructura de Strapi)
      if (typeof contenido === 'object' && contenido.children) {
        const text = contenido.children
          .filter(child => child.type === 'paragraph')
          .map(para => para.children?.map(child => child.text).join('') || '')
          .join(' ')
          .substring(0, 150)
        return text + (text.length > 150 ? '...' : '')
      }
      
      return 'Sin descripción disponible.'
    },

    normalizePost(post) {
      // Si Strapi v5 devuelve estructura con 'attributes'
      if (post.attributes) {
        return {
          id: post.id,
          ...post.attributes
        }
      }
      // Si ya viene normalizado
      return post
    }
  }
}
</script>

<style scoped>
.blog-section {
  padding: var(--spacing-3xl) 0;
  background-color: var(--color-gray-50);
}

.container {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 var(--spacing-md);
}

.blog-header {
  text-align: center;
  margin-bottom: var(--spacing-3xl);
}

.blog-header h2 {
  font-size: var(--font-size-4xl);
  color: var(--color-black);
  font-weight: var(--font-weight-bold);
  margin-bottom: var(--spacing-md);
}

.blog-subtitle {
  font-size: var(--font-size-lg);
  color: var(--color-gray-600);
  line-height: var(--line-height-relaxed);
}

/* Posts Grid */
.posts-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  gap: var(--spacing-xl);
}

.post-card {
  background-color: var(--color-white);
  border-radius: var(--border-radius-lg);
  overflow: hidden;
  box-shadow: var(--shadow-sm);
  transition: all var(--transition-fast);
  display: flex;
  flex-direction: column;
}

.post-card:hover {
  box-shadow: var(--shadow-lg);
  transform: translateY(-8px);
}

/* Post Image */
.post-image {
  width: 100%;
  height: 200px;
  background-color: var(--color-gray-200);
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
}

.post-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform var(--transition-fast);
}

.post-card:hover .post-image img {
  transform: scale(1.05);
}

.post-image.placeholder {
  font-size: var(--font-size-5xl);
  color: var(--color-gray-400);
}

/* Post Content */
.post-content {
  padding: var(--spacing-xl);
  display: flex;
  flex-direction: column;
  gap: var(--spacing-md);
  flex-grow: 1;
}

.post-title {
  font-size: var(--font-size-xl);
  color: var(--color-black);
  font-weight: var(--font-weight-bold);
  margin: 0;
  line-height: var(--line-height-tight);
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.post-excerpt {
  font-size: var(--font-size-base);
  color: var(--color-gray-600);
  margin: 0;
  line-height: var(--line-height-normal);
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  flex-grow: 1;
}

.post-link {
  display: inline-flex;
  align-items: center;
  gap: var(--spacing-sm);
  font-size: var(--font-size-base);
  font-weight: var(--font-weight-bold);
  color: var(--color-primary);
  text-decoration: none;
  transition: all var(--transition-fast);
  margin-top: auto;
}

.post-link:hover {
  color: var(--color-primary-dark);
  gap: var(--spacing-md);
}

.arrow {
  transition: transform var(--transition-fast);
}

.post-link:hover .arrow {
  transform: translateX(4px);
}

/* States */
.loading-state,
.error-state,
.empty-state {
  text-align: center;
  padding: var(--spacing-3xl) var(--spacing-xl);
  background-color: var(--color-white);
  border-radius: var(--border-radius-lg);
}

.loading-state p,
.error-state p,
.empty-state p {
  font-size: var(--font-size-lg);
  color: var(--color-gray-600);
  margin: 0;
}

.error-detail {
  font-size: var(--font-size-base);
  color: var(--color-gray-500);
  margin-top: var(--spacing-md) !important;
}

/* Responsive */
@media (max-width: 768px) {
  .blog-section {
    padding: var(--spacing-2xl) 0;
  }

  .blog-header h2 {
    font-size: var(--font-size-3xl);
  }

  .posts-grid {
    grid-template-columns: 1fr;
    gap: var(--spacing-lg);
  }

  .post-image {
    height: 150px;
  }

  .post-content {
    padding: var(--spacing-lg);
  }
}
</style>
