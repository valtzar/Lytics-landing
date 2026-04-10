<template>
  <div id="app" class="app">
    <Header />
    <Hero />
    <Features />
    <Video />
    <CTA />
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Hero from './components/Hero.vue'
import Features from './components/Features.vue'
import Video from './components/Video.vue'
import CTA from './components/CTA.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    Header,
    Hero,
    Features,
    Video,
    CTA,
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
