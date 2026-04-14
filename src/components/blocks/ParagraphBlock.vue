<template>
  <p class="paragraph">
    <template v-for="(child, index) in block.children" :key="index">
      <strong v-if="child.bold">{{ child.text }}</strong>
      <em v-else-if="child.italic">{{ child.text }}</em>
      <u v-else-if="child.underline">{{ child.text }}</u>
      <code v-else-if="child.code" class="inline-code">{{ child.text }}</code>
      <a v-else-if="child.type === 'link'" :href="child.url" target="_blank" class="link">
        {{ child.text }}
      </a>
      <span v-else>{{ child.text }}</span>
    </template>
  </p>
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
.paragraph {
  margin: 0;
  line-height: var(--line-height-relaxed);
  color: var(--color-gray-700);
}

.inline-code {
  background-color: var(--color-gray-100);
  padding: 2px 6px;
  border-radius: 3px;
  font-family: 'Courier New', monospace;
  font-size: 0.9em;
}

.link {
  color: var(--color-primary);
  text-decoration: underline;
  transition: color var(--transition-fast);
}

.link:hover {
  color: var(--color-primary-dark);
}

strong {
  font-weight: var(--font-weight-bold);
}

em {
  font-style: italic;
}

u {
  text-decoration: underline;
}
</style>
