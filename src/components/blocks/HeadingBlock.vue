<template>
  <component :is="`h${getLevel}`" :class="`heading heading-${getLevel}`">
    <template v-for="(child, index) in block.children" :key="index">
      <strong v-if="child.bold">{{ child.text }}</strong>
      <em v-else-if="child.italic">{{ child.text }}</em>
      <span v-else>{{ child.text }}</span>
    </template>
  </component>
</template>

<script setup>
defineProps({
  block: {
    type: Object,
    required: true
  }
})

const getLevel = () => {
  return (block.level || 2).toString()
}
</script>

<style scoped>
.heading {
  margin: var(--spacing-lg) 0 var(--spacing-md) 0;
  color: var(--color-black);
  font-weight: var(--font-weight-bold);
  line-height: var(--line-height-tight);
}

.heading-1 {
  font-size: var(--font-size-4xl);
}

.heading-2 {
  font-size: var(--font-size-3xl);
}

.heading-3 {
  font-size: var(--font-size-2xl);
}

.heading-4 {
  font-size: var(--font-size-xl);
}

.heading-5,
.heading-6 {
  font-size: var(--font-size-lg);
}
</style>
