<script setup>
import { ShieldCheck, Cpu, Paintbrush, Zap } from '@lucide/vue'

const pillars = [
  {
    title: 'Enterprise-Grade Development',
    desc: 'Built on 9+ years of real enterprise experience — every project, regardless of size, gets the same quality: solid architecture, clean code, and long-term maintainability.',
    icon: ShieldCheck,
    color: 'text-brand-cyan bg-brand-cyan/10 border-brand-cyan/20'
  },
  {
    title: 'Multi-Platform Delivery',
    desc: 'Web applications, mobile apps (Android & iOS via Flutter), and backend APIs — I deliver across platforms based on what your business actually needs.',
    icon: Zap,
    color: 'text-brand-blue bg-brand-blue/10 border-brand-blue/20'
  },
  {
    title: 'Workflow-First Engineering',
    desc: 'I dig into how your business actually operates before writing a single line of code. The result is software that fits your workflow — not the other way around.',
    icon: Cpu,
    color: 'text-brand-purple bg-brand-purple/10 border-brand-purple/20'
  },
  {
    title: 'Full-Cycle Ownership',
    desc: 'From requirements gathering to deployment and maintenance — I handle the full development lifecycle, so you get a reliable partner, not just a developer.',
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

      <div class="flex flex-col gap-12">
        <!-- Top: Storytelling description -->
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 lg:gap-16 text-left">
          <p class="text-neutral-300 text-sm sm:text-base leading-relaxed">
            I am a software engineer with <span class="text-white font-semibold">9+ years of hands-on experience</span> building custom ERP systems, operational platforms, web applications, and mobile apps — deployed and used daily in real business environments.
          </p>
          <p class="text-neutral-400 text-sm sm:text-base leading-relaxed">
            I work with businesses of all sizes. My enterprise background gives me the technical depth to handle complex requirements, data integrity, and long-term system stability — and I bring that same discipline to every project I take, big or small.
          </p>
        </div>

        <!-- Bottom: Four core pillars in a 4-column/2-column parallel grid -->
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6 w-full">
          <GlowCard v-for="pillar in pillars" :key="pillar.title">
            <div class="flex flex-col items-start gap-4 text-left h-full">
              <div :class="['w-10 h-10 rounded-lg flex items-center justify-center border shrink-0', pillar.color]">
                <component :is="pillar.icon" class="w-5 h-5" />
              </div>
              <div class="flex-1 flex flex-col">
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
