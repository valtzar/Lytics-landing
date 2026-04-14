<template>
  <div class="rich-text">
    <template v-if="Array.isArray(content)">
      <component
        v-for="(block, index) in content"
        :key="index"
        :is="getBlockComponent(block.type)"
        :block="block"
      />
    </template>
    <template v-else-if="typeof content === 'object' && content.children">
      <component
        v-for="(block, index) in content.children"
        :key="index"
        :is="getBlockComponent(block.type)"
        :block="block"
      />
    </template>
    <template v-else>
      <p>{{ content }}</p>
    </template>
  </div>
</template>

<script setup>
import ParagraphBlock from './blocks/ParagraphBlock.vue'
import HeadingBlock from './blocks/HeadingBlock.vue'
import ListBlock from './blocks/ListBlock.vue'
import ImageBlock from './blocks/ImageBlock.vue'
import QuoteBlock from './blocks/QuoteBlock.vue'
import CodeBlock from './blocks/CodeBlock.vue'

defineProps({
  content: {
    type: [Array, Object, String],
    required: true
  }
})

const getBlockComponent = (blockType) => {
  const componentMap = {
    'paragraph': ParagraphBlock,
    'heading': HeadingBlock,
    'list': ListBlock,
    'image': ImageBlock,
    'quote': QuoteBlock,
    'code': CodeBlock
  }

  return componentMap[blockType] || ParagraphBlock
}
</script>

<style scoped>
.rich-text {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-lg);
}
</style>
