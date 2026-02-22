<template>
  <section id="awards" class="py-24 bg-slate-800/50">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-16 scroll-reveal">
        <h2 class="font-display font-bold text-4xl md:text-5xl mb-4">Awards & Recognition</h2>
        <p class="text-slate-400 text-lg max-w-2xl mx-auto">
          Recognized globally for innovation in privacy-preserving technology
        </p>
      </div>

      <div class="grid md:grid-cols-2 gap-6 max-w-4xl mx-auto">
        <div v-for="(award, index) in awards" :key="index" 
             class="glass-card rounded-xl p-6 flex items-start space-x-4 hover-lift scroll-reveal"
             :style="{ transitionDelay: `${index * 100}ms` }">
          <div class="w-12 h-12 rounded-lg flex-shrink-0 flex items-center justify-center" :class="award.iconBg">
            <svg class="w-6 h-6" :class="award.iconColor" fill="currentColor" viewBox="0 0 20 20">
              <path fill-rule="evenodd" d="M10 2a1 1 0 011 1v1.323l3.954 1.582 1.599-.8a1 1 0 01.894 1.79l-1.233.616 1.738 5.42a1 1 0 01-.285 1.05A3.989 3.989 0 0115 15a3.989 3.989 0 01-2.667-1.019 1 1 0 01-.285-1.05l1.715-5.349L11 6.477V16h2a1 1 0 110 2H7a1 1 0 110-2h2V6.477L6.237 7.582l1.715 5.349a1 1 0 01-.285 1.05A3.989 3.989 0 015 15a3.989 3.989 0 01-2.667-1.019 1 1 0 01-.285-1.05l1.738-5.42-1.233-.616a1 1 0 01.894-1.79l1.599.8L9 4.323V3a1 1 0 011-1z" clip-rule="evenodd"/>
            </svg>
          </div>
          <div>
            <h3 class="font-display font-semibold text-lg mb-1">{{ award.title }}</h3>
            <p class="text-sm" :class="award.detailColor">{{ award.detail }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
const awards = [
  {
    title: 'Cybersecurity Project of the Year',
    detail: 'Tech Fest Hong Kong Awards 2025',
    iconBg: 'bg-yellow-500/20',
    iconColor: 'text-yellow-400',
    detailColor: 'text-primary-400',
  },
  {
    title: 'Hong Kong ITF TSSSU Grant',
    detail: '0.5M HKD | Hong Kong Innovation and Technology Commission, 2025',
    iconBg: 'bg-blue-500/20',
    iconColor: 'text-blue-400',
    detailColor: 'text-blue-400',
  },
  {
    title: 'Hong Kong ICT Award 2025',
    detail: 'FinTech Track',
    iconBg: 'bg-purple-500/20',
    iconColor: 'text-purple-400',
    detailColor: 'text-purple-400',
  },
  {
    title: 'IEEE S&P Distinguished Paper Award',
    detail: 'Premier computer security conference',
    iconBg: 'bg-red-500/20',
    iconColor: 'text-red-400',
    detailColor: 'text-red-400',
  },
]
</script>
