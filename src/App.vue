<template>
  <div id="app" class="app">
    <Header />
    <router-view />
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    Header,
    Footer
  }
}
</script>

<style scoped>
.app {
  width: 100%;
  background-color: var(--color-white);
  color: var(--color-black);
  transition: background-color var(--transition-base), color var(--transition-base);
}
</style>
