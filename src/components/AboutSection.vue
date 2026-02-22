<template>
  <section id="about" class="py-24 relative">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="grid lg:grid-cols-2 gap-16 items-center">
        <!-- Content -->
        <div class="scroll-reveal">
          <h2 class="font-display font-bold text-4xl md:text-5xl mb-6">
            Pioneering <span class="text-primary-400">Data Privacy</span> Through Advanced Research
          </h2>
          <p class="text-slate-400 text-lg leading-relaxed mb-6">
            CipherInsight is a spinoff from <strong class="text-white">HKUST's Cybersecurity Lab</strong>, 
            co-founded by researchers from <strong class="text-white">HKUST</strong> & 
            <strong class="text-white">Zhejiang University of Technology</strong>. We combine expertise in cybersecurity, 
            cloud infrastructure, and privacy-preserving systems.
          </p>
          <p class="text-slate-400 text-lg leading-relaxed mb-8">
            Our mission is to empower organizations to conduct complex data analysis while ensuring absolute 
            data confidentiality. By integrating Zero-Knowledge Proof technology with cloud-native architecture, 
            we minimize security risks and streamline analytics for regulated industries.
          </p>
          
          <!-- Team Preview with Photos -->
          <div class="flex items-center space-x-4">
            <div class="flex -space-x-3">
              <!-- Pingchuan -->
              <div class="relative w-12 h-12">
                <picture v-if="hasPhoto('pingchuan')">
                  <source :srcset="getPhotoUrl('pingchuan', 'webp')" type="image/webp">
                  <img 
                    :src="getPhotoUrl('pingchuan', 'jpg')" 
                    alt="Prof. Pingchuan Ma"
                    class="w-full h-full rounded-full object-cover border-2 border-slate-900"
                    @error="onPhotoError('pingchuan')"
                  >
                </picture>
                <div 
                  v-else
                  class="w-full h-full rounded-full bg-primary-600 flex items-center justify-center border-2 border-slate-900 text-sm font-bold"
                >
                  PM
                </div>
              </div>
              <!-- Shuai -->
              <div class="relative w-12 h-12">
                <picture v-if="hasPhoto('shuai')">
                  <source :srcset="getPhotoUrl('shuai', 'webp')" type="image/webp">
                  <img 
                    :src="getPhotoUrl('shuai', 'jpg')" 
                    alt="Prof. Shuai Wang"
                    class="w-full h-full rounded-full object-cover border-2 border-slate-900"
                    @error="onPhotoError('shuai')"
                  >
                </picture>
                <div 
                  v-else
                  class="w-full h-full rounded-full bg-accent-600 flex items-center justify-center border-2 border-slate-900 text-sm font-bold"
                >
                  SW
                </div>
              </div>
              <!-- Zongjie -->
              <div class="relative w-12 h-12">
                <picture v-if="hasPhoto('zongjie')">
                  <source :srcset="getPhotoUrl('zongjie', 'webp')" type="image/webp">
                  <img 
                    :src="getPhotoUrl('zongjie', 'jpg')" 
                    alt="Dr. Zongjie Li"
                    class="w-full h-full rounded-full object-cover border-2 border-slate-900"
                    @error="onPhotoError('zongjie')"
                  >
                </picture>
                <div 
                  v-else
                  class="w-full h-full rounded-full bg-green-600 flex items-center justify-center border-2 border-slate-900 text-sm font-bold"
                >
                  ZL
                </div>
              </div>
            </div>
            <div class="text-sm text-slate-400">
              <span class="text-white font-medium">3 Co-Founders</span><br>
              HKUST, ZJUT
            </div>
          </div>
        </div>

        <!-- Cards -->
        <div class="grid gap-6 scroll-reveal">
          <div v-for="(feature, index) in features" :key="index" class="glass-card rounded-2xl p-6 hover-lift">
            <div class="w-12 h-12 rounded-xl bg-opacity-20 flex items-center justify-center mb-4" :class="feature.iconBg">
              <svg class="w-6 h-6" :class="feature.iconColor" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" :d="feature.icon"/>
              </svg>
            </div>
            <h3 class="font-display font-semibold text-xl mb-2">{{ feature.title }}</h3>
            <p class="text-slate-400">{{ feature.description }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

// Track which photos failed to load
const failedPhotos = ref<Set<string>>(new Set())

// Check if photo file exists
onMounted(async () => {
  const founders = ['pingchuan', 'shuai', 'zongjie']
  for (const founder of founders) {
    try {
      const response = await fetch(getPhotoUrl(founder, 'webp'), { method: 'HEAD' })
      if (!response.ok) {
        const jpgResponse = await fetch(getPhotoUrl(founder, 'jpg'), { method: 'HEAD' })
        if (!jpgResponse.ok) {
          failedPhotos.value.add(founder)
        }
      }
    } catch {
      failedPhotos.value.add(founder)
    }
  }
})

const getPhotoUrl = (founder: string, format: 'webp' | 'jpg') => `/founders/${founder}.${format}`

const hasPhoto = (founder: string) => !failedPhotos.value.has(founder)

const onPhotoError = (founder: string) => {
  failedPhotos.value.add(founder)
}

const features = [
  {
    title: 'Absolute Privacy',
    description: 'Zero-Knowledge Proofs ensure data never leaves your control while enabling powerful analytics.',
    icon: 'M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z',
    iconBg: 'bg-primary-500',
    iconColor: 'text-primary-400',
  },
  {
    title: 'Cloud-Native',
    description: 'Built for the cloud with scalable architecture that grows with your data needs.',
    icon: 'M13 10V3L4 14h7v7l9-11h-7z',
    iconBg: 'bg-accent-500',
    iconColor: 'text-accent-400',
  },
  {
    title: 'Compliance Ready',
    description: 'Meet stringent regulatory requirements including cross-border data transfer regulations.',
    icon: 'M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z',
    iconBg: 'bg-green-500',
    iconColor: 'text-green-400',
  },
]
</script>
