<template>
  <div id="app" class="app">
    <Header />
    <Hero />
    <Personalization />
    <Features />
    <IntelligentAlerts />
    <PremiumService />
    <Video />
    <ManagerBenefits />
    <CTA />
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Hero from './components/Hero.vue'
import Personalization from './components/Personalization.vue'
import Features from './components/Features.vue'
import IntelligentAlerts from './components/IntelligentAlerts.vue'
import PremiumService from './components/PremiumService.vue'
import Video from './components/Video.vue'
import ManagerBenefits from './components/ManagerBenefits.vue'
import CTA from './components/CTA.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    Header,
    Hero,
    Personalization,
    Features,
    IntelligentAlerts,
    PremiumService,
    Video,
    ManagerBenefits,
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
