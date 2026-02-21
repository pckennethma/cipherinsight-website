<template>
  <section class="py-24 bg-slate-800/50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-16 scroll-reveal">
        <h2 class="font-display font-bold text-4xl md:text-5xl mb-4">Meet Our Founders</h2>
        <p class="text-slate-400 text-lg max-w-2xl mx-auto">World-leading experts in computer security and privacy-preserving systems</p>
      </div>

      <div class="grid md:grid-cols-3 gap-8">
        <!-- Prof. Pingchuan Ma -->
        <div class="glass-card rounded-2xl p-8 text-center hover-lift scroll-reveal">
          <div class="relative w-24 h-24 mx-auto mb-6">
            <img 
              v-if="hasPhoto('pingchuan')"
              :src="getPhotoUrl('pingchuan')" 
              alt="Prof. Pingchuan Ma"
              class="w-full h-full rounded-full object-cover"
              @error="onPhotoError('pingchuan')"
            >
            <div 
              v-else
              class="w-full h-full rounded-full bg-gradient-to-br from-primary-500 to-primary-700 flex items-center justify-center text-3xl font-bold"
            >
              PM
            </div>
          </div>
          <h3 class="font-display font-bold text-xl mb-1">Prof. Pingchuan Ma</h3>
          <p class="text-primary-400 text-sm mb-4">Co-Founder</p>
          <div class="text-slate-400 text-sm space-y-2 text-left">
            <p><strong class="text-white">Professor</strong> at Zhejiang University of Technology</p>
            <p>Ph.D. from HKUST</p>
            <p class="pt-2 border-t border-white/10 mt-2">Research: Privacy-enhancing Technology, Data Science</p>
            <p class="text-xs text-primary-400">NSFC Excellent Young Scientists Program (Overseas)</p>
          </div>
        </div>

        <!-- Prof. Shuai Wang -->
        <div class="glass-card rounded-2xl p-8 text-center hover-lift scroll-reveal" style="transition-delay: 100ms;">
          <div class="relative w-24 h-24 mx-auto mb-6">
            <img 
              v-if="hasPhoto('shuai')"
              :src="getPhotoUrl('shuai')" 
              alt="Prof. Shuai Wang"
              class="w-full h-full rounded-full object-cover"
              @error="onPhotoError('shuai')"
            >
            <div 
              v-else
              class="w-full h-full rounded-full bg-gradient-to-br from-accent-500 to-accent-700 flex items-center justify-center text-3xl font-bold"
            >
              SW
            </div>
          </div>
          <h3 class="font-display font-bold text-xl mb-1">Prof. Shuai Wang</h3>
          <p class="text-accent-400 text-sm mb-4">Co-Founder</p>
          <div class="text-slate-400 text-sm space-y-2 text-left">
            <p><strong class="text-white">Associate Professor (Tenured)</strong> at CSE, HKUST</p>
            <p>Ph.D. from Penn State University</p>
            <p class="pt-2 border-t border-white/10 mt-2">Research: Computer Security & Privacy, Software Engineering, AI Systems</p>
            <p class="text-xs text-accent-400">Google Research Scholar Award (2023), HK-UGC Early Career Award (2020)</p>
          </div>
        </div>

        <!-- Dr. Zongjie Li -->
        <div class="glass-card rounded-2xl p-8 text-center hover-lift scroll-reveal" style="transition-delay: 200ms;">
          <div class="relative w-24 h-24 mx-auto mb-6">
            <img 
              v-if="hasPhoto('zongjie')"
              :src="getPhotoUrl('zongjie')" 
              alt="Dr. Zongjie Li"
              class="w-full h-full rounded-full object-cover"
              @error="onPhotoError('zongjie')"
            >
            <div 
              v-else
              class="w-full h-full rounded-full bg-gradient-to-br from-green-500 to-green-700 flex items-center justify-center text-3xl font-bold"
            >
              ZL
            </div>
          </div>
          <h3 class="font-display font-bold text-xl mb-1">Dr. Zongjie Li</h3>
          <p class="text-green-400 text-sm mb-4">Co-Founder</p>
          <div class="text-slate-400 text-sm space-y-2 text-left">
            <p><strong class="text-white">Postdoc</strong> at HKUST</p>
            <p>Ph.D. from HKUST</p>
            <p class="pt-2 border-t border-white/10 mt-2">Research: LLMs for Code, Software Security</p>
            <p class="text-xs text-green-400">2025 Ant InTech Technology Scholarship</p>
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

// Check if photo file exists (by trying to fetch it)
onMounted(async () => {
  const founders = ['pingchuan', 'shuai', 'zongjie']
  for (const founder of founders) {
    try {
      const response = await fetch(getPhotoUrl(founder), { method: 'HEAD' })
      if (!response.ok) {
        failedPhotos.value.add(founder)
      }
    } catch {
      // If fetch fails (network error, etc.), assume photo doesn't exist
      failedPhotos.value.add(founder)
    }
  }
})

const getPhotoUrl = (founder: string) => `/founders/${founder}.jpg`

const hasPhoto = (founder: string) => !failedPhotos.value.has(founder)

const onPhotoError = (founder: string) => {
  failedPhotos.value.add(founder)
}
</script>
