<script setup>
import { Layout, Server, Database, Settings } from '@lucide/vue'

const categories = [
  {
    name: 'Backend Architecture',
    icon: Server,
    color: 'text-brand-cyan bg-brand-cyan/5 border-brand-cyan/15',
    items: ['System Design','Node.js', 'Laravel', 'PHP', 'Express', 'RESTful APIs']
  },
  {
    name: 'Frontend & Mobile',
    icon: Layout,
    color: 'text-brand-blue bg-brand-blue/5 border-brand-blue/15',
    items: ['Vue.js', 'Nuxt.js', 'Tailwind CSS', 'Flutter','Figma', 'Responsive Design']
  },
  {
    name: 'Database Engineering',
    icon: Database,
    color: 'text-brand-purple bg-brand-purple/5 border-brand-purple/15',
    items: ['MySQL', 'MongoDB', 'Database Design', 'Query Optimization', 'Data Migrations','Automated Backups']
  },
  {
    name: 'Infrastructure & DevOps',
    icon: Settings,
    color: 'text-brand-emerald bg-brand-emerald/5 border-brand-emerald/15',
    items: ['Docker', 'Linux', 'Nginx', 'PM2', 'CI/CD Pipelines','Server Monitoring', 'Performance Optimization','Security Hardening']
  }
]
</script>

<template>
  <section id="tech-stack" class="py-24 relative overflow-hidden bg-neutral-950/20 border-t border-white/5">
    <div class="max-w-7xl mx-auto px-6 relative z-10">
      
      <!-- Section Header -->
      <div class="flex flex-col items-start gap-4 mb-16 max-w-xl text-left">
        <span class="text-xs font-mono font-semibold uppercase tracking-widest text-neutral-500">Expertise Stack</span>
        <h2 class="text-3xl sm:text-4xl font-bold tracking-tight text-white leading-tight">
          Tools of the Trade
        </h2>
        <div class="h-1 w-12 bg-gradient-to-r from-brand-blue to-brand-purple rounded-full"></div>
      </div>

      <!-- Categories Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
        <GlowCard v-for="cat in categories" :key="cat.name">
          <div class="flex flex-col gap-6 text-left h-full justify-between">
            
            <!-- Category Title & Icon -->
            <div class="flex items-center gap-3">
              <div :class="['w-10 h-10 rounded-lg flex items-center justify-center border', cat.color]">
                <component :is="cat.icon" class="w-5 h-5" />
              </div>
              <h3 class="text-sm font-bold text-white font-mono tracking-wide uppercase">
                {{ cat.name }}
              </h3>
            </div>

            <!-- Tech Badges Grid -->
            <div class="flex flex-wrap gap-2.5 mt-2">
              <span
                v-for="item in cat.items"
                :key="item"
                class="px-3.5 py-2 rounded-lg bg-neutral-950 border border-white/5 text-neutral-300 text-xs font-medium font-mono hover:text-white hover:border-white/15 hover:bg-neutral-900/60 transition-all duration-200 select-none shadow-inner"
              >
                {{ item }}
              </span>
            </div>

          </div>
        </GlowCard>
      </div>

    </div>
  </section>
</template>
