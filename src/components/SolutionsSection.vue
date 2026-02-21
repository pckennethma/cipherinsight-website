<template>
  <section id="solutions" class="py-24 relative">
    <div class="absolute inset-0 bg-gradient-to-b from-slate-900 via-slate-800/30 to-slate-900"></div>
    <div class="relative max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-16 scroll-reveal">
        <h2 class="font-display font-bold text-4xl md:text-5xl mb-4">Our Solutions</h2>
        <p class="text-slate-400 text-lg max-w-2xl mx-auto">
          Comprehensive ZKP-powered infrastructure for privacy-enhancing analytics
        </p>
      </div>

      <div class="grid md:grid-cols-3 gap-8">
        <div v-for="(solution, index) in solutions" :key="index" 
             class="group relative scroll-reveal"
             :style="{ transitionDelay: `${index * 100}ms` }">
          <div class="absolute inset-0 bg-gradient-to-r rounded-2xl blur-xl opacity-20 group-hover:opacity-40 transition-opacity"
               :class="solution.gradient"></div>
          <div class="relative glass-card rounded-2xl p-8 h-full">
            <div class="w-14 h-14 rounded-xl bg-opacity-20 flex items-center justify-center mb-6 group-hover:scale-110 transition-transform"
                 :class="solution.iconBg">
              <svg class="w-7 h-7" :class="solution.iconColor" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" :d="solution.icon"/>
              </svg>
            </div>
            <h3 class="font-display font-bold text-2xl mb-3">{{ solution.title }}</h3>
            <p class="text-slate-400 leading-relaxed mb-6">{{ solution.description }}</p>
            <ul class="space-y-2">
              <li v-for="(feature, fIndex) in solution.features" :key="fIndex" class="flex items-center text-sm text-slate-300">
                <svg class="w-5 h-5 mr-2" :class="solution.iconColor" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"/>
                </svg>
                {{ feature }}
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
const solutions = [
  {
    title: 'ZK Data Science',
    description: 'Privacy-preserving data analytics solution that enables organizations to derive insights from sensitive data without compromising confidentiality.',
    icon: 'M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z',
    gradient: 'from-primary-600 to-primary-400',
    iconBg: 'bg-primary-500',
    iconColor: 'text-primary-400',
    features: ['Verifiable computation', 'Cross-border analytics', 'Regulatory compliance'],
  },
  {
    title: 'ZK Programming Toolchain',
    description: 'Developer-friendly tools for building ZKP applications with familiar interfaces. No cryptographic expertise required.',
    icon: 'M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4',
    gradient: 'from-accent-600 to-accent-400',
    iconBg: 'bg-accent-500',
    iconColor: 'text-accent-400',
    features: ['Familiar syntax', 'Auto-optimization', 'Tensor operations'],
  },
  {
    title: 'ZK Proving-as-a-Service',
    description: 'Scalable, distributed proof generation infrastructure that handles the computational complexity of ZKP generation.',
    icon: 'M19 11H5m14 0a2 2 0 012 2v6a2 2 0 01-2 2H5a2 2 0 01-2-2v-6a2 2 0 012-2m14 0V9a2 2 0 00-2-2M5 11V9a2 2 0 012-2m0 0V5a2 2 0 012-2h6a2 2 0 012 2v2M7 7h10',
    gradient: 'from-green-600 to-green-400',
    iconBg: 'bg-green-500',
    iconColor: 'text-green-400',
    features: ['Distributed proving', 'Cost-efficient', 'Auto-scaling'],
  },
]
</script>
