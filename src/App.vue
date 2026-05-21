<script setup lang="ts">
import SiteHeader from '@/components/layout/SiteHeader.vue'
import SiteFooter from '@/components/layout/SiteFooter.vue'
import HeroSection from '@/components/sections/HeroSection.vue'
import ProblemsSection from '@/components/sections/ProblemsSection.vue'
import ServicesSection from '@/components/sections/ServicesSection.vue'
import QualificationsSection from '@/components/sections/QualificationsSection.vue'
import ContactSection from '@/components/sections/ContactSection.vue'
</script>

<template>
  <div class="app">
    <SiteHeader />
    <main>
      <HeroSection />
      <ProblemsSection />
      <ServicesSection />
      <QualificationsSection />
      <ContactSection />
    </main>
    <SiteFooter />
  </div>
</template>

<style scoped>
.app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

main {
  flex: 1;
}
</style>
