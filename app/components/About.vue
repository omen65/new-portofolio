<script setup>
import { ShieldCheck, Cpu, Paintbrush, Zap } from '@lucide/vue'

const pillars = [
  {
    title: 'Production-First Ethos',
    desc: 'I prefer building complete, multi-tenant databases and integrated ledger systems rather than trivial landing page templates.',
    icon: ShieldCheck,
    color: 'text-brand-cyan bg-brand-cyan/10 border-brand-cyan/20'
  },
  {
    title: 'Dual Creative & Technical Stack',
    desc: 'Equally comfortable designing modern graphic assets and vector arts as writing REST APIs, SQL transactions, or server configurations.',
    icon: Paintbrush,
    color: 'text-brand-blue bg-brand-blue/10 border-brand-blue/20'
  },
  {
    title: 'DevOps & Infrastructure Care',
    desc: 'From initial Docker containerization to setting up PM2 clusters and Nginx proxy servers, I deploy and manage my own infrastructure.',
    icon: Cpu,
    color: 'text-brand-purple bg-brand-purple/10 border-brand-purple/20'
  },
  {
    title: 'Workflow Automation',
    desc: 'Active designer of custom scripting workflows, programmatic AI pipelines, and custom content generation systems to speed up output.',
    icon: Zap,
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
            I am a software engineer with <span class="text-white font-semibold">10+ years of active experience</span> building scalable web systems, digital platforms, and production-level tools. Rather than chasing tutorial demos, I enjoy engineering business-critical backbones that solve real-world logistical problems.
          </p>
          <p class="text-neutral-400 text-sm sm:text-base leading-relaxed">
            Alongside coding, I operate as a freelance graphic designer and active microstock creator, designing visual concepts, digital layouts, and AI-assisted vector packages for various platforms. This blend of structured logical architecture and artistic creative skills allows me to develop applications that are both structurally powerful and visually engaging.
          </p>

          <!-- Core stats overview -->
          <div class="grid grid-cols-2 gap-4 mt-4">
            <div class="p-4 rounded-xl border border-white/5 bg-neutral-900/30">
              <span class="block text-2xl font-bold text-white font-mono">10y+</span>
              <span class="text-xs text-neutral-500 uppercase tracking-wider font-mono">Active Coding</span>
            </div>
            <div class="p-4 rounded-xl border border-white/5 bg-neutral-900/30">
              <span class="block text-2xl font-bold text-white font-mono">15k+</span>
              <span class="text-xs text-neutral-500 uppercase tracking-wider font-mono">Vectors &amp; Graphics</span>
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
