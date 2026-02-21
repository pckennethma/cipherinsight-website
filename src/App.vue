<template>
  <div class="min-h-screen overflow-x-hidden">
    <NavigationBar />
    <main>
      <HeroSection />
      <AboutSection />
      <TeamSection />
      <SolutionsSection />
      <AwardsSection />
      <PublicationsSection />
      <ContactSection />
    </main>
    <FooterSection />
  </div>
</template>

<script setup lang="ts">
import { onMounted } from 'vue'
import NavigationBar from './components/NavigationBar.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import TeamSection from './components/TeamSection.vue'
import SolutionsSection from './components/SolutionsSection.vue'
import AwardsSection from './components/AwardsSection.vue'
import PublicationsSection from './components/PublicationsSection.vue'
import ContactSection from './components/ContactSection.vue'
import FooterSection from './components/FooterSection.vue'

onMounted(() => {
  // Scroll reveal animation
  const observerOptions = {
    threshold: 0.1,
    rootMargin: '0px 0px -50px 0px'
  }

  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('revealed')
      }
    })
  }, observerOptions)

  document.querySelectorAll('.scroll-reveal').forEach(el => observer.observe(el))
})
</script>
