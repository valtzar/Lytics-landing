<template>
  <div class="logo-wrapper" :style="{ height: height }">
    <img 
      src="@/assets/Logo LYTICS.svg" 
      alt="Lytics - Desarrollo organizacional inteligente"
      class="logo-image"
    />
  </div>
</template>

<script>
export default {
  name: 'Logo',
  props: {
    height: {
      type: String,
      default: '80px'
    }
  }
}
</script>

<style scoped>
.logo-wrapper {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  width: 100%;
}

.logo-image {
  width: auto;
  height: 100%;
  max-width: 100%;
  display: block;
}
</style>
