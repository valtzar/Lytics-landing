<template>
  <div class="image-block">
    <img
      v-if="imageUrl"
      :src="imageUrl"
      :alt="block.caption || 'Imagen del artículo'"
      class="image"
    />
    <p v-if="block.caption" class="image-caption">{{ block.caption }}</p>
  </div>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  block: {
    type: Object,
    required: true
  }
})

const imageUrl = computed(() => {
  const image = props.block.image
  if (!image) return null
  
  const url = image.url || image.formats?.large?.url || image.formats?.medium?.url
  if (!url) return null
  
  if (url.startsWith('http')) {
    return url
  }
  
  return `http://localhost:1337${url}`
})
</script>

<style scoped>
.image-block {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-md);
  margin: var(--spacing-2xl) 0;
}

.image {
  width: 100%;
  height: auto;
  border-radius: var(--border-radius-lg);
  box-shadow: var(--shadow-md);
}

.image-caption {
  font-size: var(--font-size-sm);
  color: var(--color-gray-600);
  text-align: center;
  margin: 0;
  font-style: italic;
}
</style>
