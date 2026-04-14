<template>
  <ul v-if="block.format === 'unordered'" class="list unordered-list">
    <li v-for="(item, index) in block.children" :key="index">
      <template v-for="(child, idx) in item.children" :key="idx">
        {{ child.text }}
      </template>
    </li>
  </ul>
  <ol v-else class="list ordered-list">
    <li v-for="(item, index) in block.children" :key="index">
      <template v-for="(child, idx) in item.children" :key="idx">
        {{ child.text }}
      </template>
    </li>
  </ol>
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
.list {
  margin: var(--spacing-md) 0;
  padding-left: var(--spacing-xl);
  color: var(--color-gray-700);
}

.unordered-list {
  list-style-type: disc;
}

.ordered-list {
  list-style-type: decimal;
}

li {
  margin: var(--spacing-sm) 0;
  line-height: var(--line-height-relaxed);
}
</style>
