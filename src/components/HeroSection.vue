<template>
  <section class="relative min-h-screen flex items-center justify-center pt-20 overflow-hidden">
    <!-- Animated SVG Background -->
    <div class="absolute inset-0 z-0">
      <img 
        src="/hero-bg.svg" 
        alt="" 
        class="w-full h-full object-cover"
        style="position: absolute; inset: 0;"
      >
    </div>

    <div class="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
      <div class="scroll-reveal">
        <!-- Badge -->
        <div class="inline-flex items-center px-4 py-2 rounded-full bg-white/5 border border-white/10 mb-8">
          <span class="w-2 h-2 rounded-full bg-green-400 mr-2 animate-pulse"></span>
          <span class="text-sm text-slate-300">HKUST Cybersecurity Lab Spinoff</span>
        </div>
        
        <!-- Headline -->
        <h1 class="font-display font-bold text-5xl md:text-7xl lg:text-8xl leading-tight mb-6">
          <span class="block">Privacy-Preserving</span>
          <span class="gradient-text">Analytics</span>
          <span class="block text-4xl md:text-6xl lg:text-7xl mt-2 text-slate-400">for the Modern Era</span>
        </h1>
        
        <!-- Description -->
        <p class="max-w-3xl mx-auto text-lg md:text-xl text-slate-400 mb-12 leading-relaxed">
          Empowering organizations to unlock the full potential of sensitive data through 
          <span class="text-primary-400 font-medium">Zero-Knowledge Proof</span> technology — 
          ensuring absolute confidentiality while driving actionable insights.
        </p>

        <!-- CTA Buttons -->
        <div class="flex flex-col sm:flex-row items-center justify-center gap-4">
          <a href="#solutions" class="px-8 py-4 bg-primary-600 hover:bg-primary-500 rounded-full font-semibold text-lg transition-all hover:scale-105 shadow-lg shadow-primary-600/25">
            Explore Our Solutions
          </a>
          <a href="#about" class="px-8 py-4 bg-white/5 hover:bg-white/10 border border-white/20 rounded-full font-semibold text-lg transition-all">
            Learn More
          </a>
        </div>
      </div>

      <!-- Stats -->
      <div class="grid grid-cols-2 md:grid-cols-4 gap-8 mt-20 pt-12 border-t border-white/10 scroll-reveal">
        <div v-for="stat in stats" :key="stat.label">
          <div class="font-display font-bold text-3xl md:text-4xl text-white">{{ stat.value }}</div>
          <div class="text-slate-400 text-sm mt-1">{{ stat.label }}</div>
        </div>
      </div>
    </div>

    <!-- Scroll Indicator -->
    <div class="absolute bottom-8 left-1/2 transform -translate-x-1/2 animate-bounce">
      <svg class="w-6 h-6 text-slate-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"/>
      </svg>
    </div>
  </section>
</template>

<script setup lang="ts">
const stats = [
  { value: 'ZKP', label: 'Zero-Knowledge Tech' },
  { value: 'Cloud', label: 'Native Architecture' },
  { value: 'FinTech', label: 'Focus Area' },
  { value: 'HKUST', label: 'Research Origin' },
]
</script>
