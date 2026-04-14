<template>
  <blockquote class="quote-block">
    <p>
      <template v-for="(child, index) in block.children" :key="index">
        {{ child.text }}
      </template>
    </p>
    <footer v-if="block.author" class="quote-author">— {{ block.author }}</footer>
  </blockquote>
</template>

<script setup>
defineProps({
  block: {
    type: Object,
    required: true
  }
})
</script>

<style scoped>
.quote-block {
  border-left: 4px solid var(--color-primary);
  padding-left: var(--spacing-lg);
  margin: var(--spacing-2xl) 0;
  font-style: italic;
  color: var(--color-gray-700);
}

.quote-block p {
  margin: 0 0 var(--spacing-sm) 0;
  line-height: var(--line-height-relaxed);
}

.quote-author {
  font-size: var(--font-size-sm);
  color: var(--color-gray-600);
  margin: 0;
  font-style: normal;
}
</style>
