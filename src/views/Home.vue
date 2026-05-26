<template>
  <div class="home">
    <Video />
    <Hero />
    <Personalization />
    <Features />
    <IntelligentAlerts />
    <PremiumService />
    <ManagerBenefits />
    <Contact />
    <CTA />
  </div>
</template>

<script>
import Video from '../components/Video.vue'
import Hero from '../components/Hero.vue'
import Personalization from '../components/Personalization.vue'
import Features from '../components/Features.vue'
import IntelligentAlerts from '../components/IntelligentAlerts.vue'
import PremiumService from '../components/PremiumService.vue'
import ManagerBenefits from '../components/ManagerBenefits.vue'
import Contact from '../components/Contact.vue'
import CTA from '../components/CTA.vue'

export default {
  name: 'Home',
  components: {
    Video,
    Hero,
    Personalization,
    Features,
    IntelligentAlerts,
    PremiumService,
    ManagerBenefits,
    Contact,
    CTA
  }
}
</script>

<style scoped>
.home {
  width: 100%;
}
</style>
