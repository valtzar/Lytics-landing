<template>
  <pre class="code-block"><code>
    <template v-for="(child, index) in block.children" :key="index">{{ child.text }}</template>
  </code></pre>
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
.code-block {
  background-color: var(--color-gray-900);
  color: #e8e8e8;
  padding: var(--spacing-lg);
  border-radius: var(--border-radius-md);
  overflow-x: auto;
  margin: var(--spacing-lg) 0;
  font-family: 'Courier New', 'Monaco', monospace;
  font-size: 14px;
  line-height: 1.5;
}

code {
  display: block;
  white-space: pre;
}
</style>
