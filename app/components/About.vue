<script setup>
import { ShieldCheck, Cpu, Paintbrush, Zap } from '@lucide/vue'

const pillars = [
  {
    title: 'Enterprise Architecture',
    desc: 'Designing scalable databases and robust backends to support complex business workflows and large-scale data processing.',
    icon: ShieldCheck,
    color: 'text-brand-cyan bg-brand-cyan/10 border-brand-cyan/20'
  },
  {
    title: 'Operational Efficiency',
    desc: 'Automating workflows, digitizing manual business processes, and building reliable internal tools to drive company productivity.',
    icon: Zap,
    color: 'text-brand-blue bg-brand-blue/10 border-brand-blue/20'
  },
  {
    title: 'Full-Cycle Development',
    desc: 'From initial requirement gathering with management to long-term system maintenance and scalable deployments.',
    icon: Cpu,
    color: 'text-brand-purple bg-brand-purple/10 border-brand-purple/20'
  },
  {
    title: 'Technical Leadership',
    desc: 'Leading engineering teams, conducting code reviews, defining technical strategies, and mentoring junior engineers.',
    icon: ShieldCheck,
    color: 'text-brand-emerald bg-brand-emerald/10 border-brand-emerald/20'
  }
]
</script>

<template>
  <section id="about" class="py-24 relative overflow-hidden bg-neutral-950/40">
    <div class="absolute inset-0 mesh-glow-3 pointer-events-none"></div>

    <div class="max-w-7xl mx-auto px-6 relative z-10">
      
      <!-- Section Header -->
      <div class="flex flex-col items-start gap-4 mb-16 max-w-xl text-left">
        <span class="text-xs font-mono font-semibold uppercase tracking-widest text-neutral-500">Ethos &amp; Story</span>
        <h2 class="text-3xl sm:text-4xl font-bold tracking-tight text-white leading-tight">
          Behind Feri Anggriawan
        </h2>
        <div class="h-1 w-12 bg-gradient-to-r from-brand-cyan to-brand-blue rounded-full"></div>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-12 gap-16 items-start">
        
        <!-- Left Side: Long-form storytelling -->
        <div class="lg:col-span-6 flex flex-col gap-6 text-left">
          <p class="text-neutral-300 text-sm sm:text-base leading-relaxed">
            I am a senior enterprise software engineer with <span class="text-white font-semibold">9+ years of experience</span> designing and developing custom ERP systems, operational platforms, and internal mobile applications. I specialize in architecting business-critical software that solves complex logistical and operational challenges.
          </p>
          <p class="text-neutral-400 text-sm sm:text-base leading-relaxed">
            My engineering philosophy centers on deep collaboration with management and end-users to understand real-world workflows. I focus on building scalable, reliable, and secure internal platforms that optimize business processes, ensuring long-term maintainability and seamless cross-departmental integration.
          </p>

          <!-- Core stats overview -->
          <div class="grid grid-cols-2 gap-4 mt-4">
            <div class="p-4 rounded-xl border border-white/5 bg-neutral-900/30">
              <span class="block text-2xl font-bold text-white font-mono">9y+</span>
              <span class="text-xs text-neutral-500 uppercase tracking-wider font-mono">Active Coding</span>
            </div>
            <div class="p-4 rounded-xl border border-white/5 bg-neutral-900/30">
              <span class="block text-2xl font-bold text-white font-mono">100%</span>
              <span class="text-xs text-neutral-500 uppercase tracking-wider font-mono">Custom Built Apps</span>
            </div>
          </div>
        </div>

        <!-- Right Side: Four core pillars -->
        <div class="lg:col-span-6 grid grid-cols-1 sm:grid-cols-2 gap-6 w-full">
          <GlowCard v-for="pillar in pillars" :key="pillar.title">
            <div class="flex flex-col items-start gap-4 text-left">
              <div :class="['w-10 h-10 rounded-lg flex items-center justify-center border', pillar.color]">
                <component :is="pillar.icon" class="w-5 h-5" />
              </div>
              <div>
                <h3 class="text-sm font-semibold text-white tracking-tight mb-2">
                  {{ pillar.title }}
                </h3>
                <p class="text-neutral-400 text-xs leading-relaxed">
                  {{ pillar.desc }}
                </p>
              </div>
            </div>
          </GlowCard>
        </div>

      </div>

    </div>
  </section>
</template>
