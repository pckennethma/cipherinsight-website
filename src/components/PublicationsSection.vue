<template>
  <section id="publications" class="py-24">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="text-center mb-16 scroll-reveal">
        <h2 class="font-display font-bold text-4xl md:text-5xl mb-4">Research Publications</h2>
        <p class="text-slate-400 text-lg max-w-2xl mx-auto">
          Cutting-edge research driving innovation in zero-knowledge technology
        </p>
      </div>

      <div class="space-y-6 max-w-4xl mx-auto">
        <div v-for="(pub, index) in publications" :key="index" 
             class="glass-card rounded-xl p-6 md:p-8 hover-lift scroll-reveal"
             :style="{ transitionDelay: `${index * 100}ms` }">
          <div class="flex items-start space-x-4">
            <div class="w-10 h-10 rounded-lg flex-shrink-0 flex items-center justify-center" :class="pub.numberBg">
              <span class="font-bold" :class="pub.numberColor">{{ String(index + 1).padStart(2, '0') }}</span>
            </div>
            <div>
              <h3 class="font-display font-semibold text-lg mb-2 text-white">
                {{ pub.title }}
              </h3>
              <p class="text-slate-400 text-sm mb-3">{{ pub.authors }}</p>
              <p class="text-sm" :class="pub.venueColor">{{ pub.venue }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
const publications = [
  {
    title: 'Privacy-preserving and Verifiable Causal Prescriptive Analytics',
    authors: 'Z Wang, P Ma, Z Xue, Y Dai, Z Ji, S Wang',
    venue: 'Proceedings of the ACM on Management of Data 3 (6), 1-27',
    numberBg: 'bg-primary-500/20',
    numberColor: 'text-primary-400',
    venueColor: 'text-primary-400',
  },
  {
    title: 'From Evaluation to Enhancement: Large Language Models for Zero-Knowledge Proof Code Generation',
    authors: 'Z Xue, P Ma, Z Wang, Y Zhou, X Zhang, S Wang, J Rahmel',
    venue: 'arXiv preprint arXiv:2509.11708',
    numberBg: 'bg-accent-500/20',
    numberColor: 'text-accent-400',
    venueColor: 'text-accent-400',
  },
  {
    title: 'Zinnia: An Expressive and Efficient Tensor-Oriented Zero-Knowledge Programming Framework',
    authors: 'Z Xue, P Ma, Z Wang, S Wang',
    venue: 'IACR Cryptol. ePrint Arch. 2025, 572',
    numberBg: 'bg-green-500/20',
    numberColor: 'text-green-400',
    venueColor: 'text-green-400',
  },
]
</script>
