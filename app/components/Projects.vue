<script setup>
import { ref } from 'vue'
import { Terminal, Paintbrush, ArrowUpRight, CheckCircle2 } from '@lucide/vue'

const activeTab = ref('software')

const softwareProjects = [
  {
    title: 'Distributor Inventory & Sales System',
    description: 'A comprehensive, SaaS-ready distributor inventory and sales architecture built with Laravel and Filament. Engineered for multi-entity distribution chains with rigorous stock accounting controls.',
    techs: ['Laravel', 'Filament', 'MySQL'],
    highlights: [
      'Multi-warehouse synchronization',
      'FIFO inventory valuation mechanism',
      'Comprehensive real-time stock ledger',
      'Purchase & sales pipelines',
      'Unified reporting infrastructure',
      'Multi-tenant SaaS-ready architecture'
    ]
  },
  {
    title: 'University Lab Information System',
    description: 'An integrated laboratory operations suite for educational institutions. Designed to manage physical lab inventory, schedule student reservations, log equipment usage, and trace student attendance.',
    techs: ['Laravel', 'Vue.js', 'MySQL'],
    highlights: [
      'Inventory control & asset tagging',
      'Interactive lab calendar scheduler',
      'Equipment loan approval flow',
      'Unified attendance tracker',
      'Multi-institution tenant separation'
    ]
  },
  {
    title: 'Digital Invitation Platform',
    description: 'A custom, commercial digital invitation template builder running in active production since 2022. Handles organic transactions and provides instant custom layout distribution.',
    techs: ['PHP', 'JavaScript', 'MySQL'],
    highlights: [
      'Organic paid customer transactions',
      'Integrated checkout payment flow',
      'Instant digital asset rendering',
      'Dynamic builder template modules',
      'Whitelabel custom invitation sites'
    ]
  },
  {
    title: 'Automation & AI Tools',
    description: 'A specialized cluster of automated batching scripts and intelligence pipelines designed to automate content creation and microstock asset preparation.',
    techs: ['Node.js', 'Automation APIs', 'AI APIs'],
    highlights: [
      'AI-assisted script generator pipeline',
      'Multi-channel API sync pipeline',
      'Automatic tagging & categorization',
      'Internal developer productivity plugins'
    ]
  }
]

const designProjects = [
  {
    title: 'Apex Modern SaaS UI Kit',
    description: 'A premium, comprehensive design system crafted in Figma for next-generation dark-themed SaaS platforms, dashboards, and developer portals.',
    techs: ['Figma', 'UI Design', 'Design Tokens'],
    highlights: [
      'Advanced component variants & variables',
      'Clean minimalist dark-mode designs',
      '150+ responsive layout modules',
      'Extensive interactive status previews',
      'Scalable token design infrastructure'
    ]
  },
  {
    title: 'Aether Premium Dark Theme',
    description: 'A curated collection of minimalist dark UI assets, vector icons, and sleek style templates featured in leading digital asset markets.',
    techs: ['Illustrator', 'Theme Assets', 'Vector Art'],
    highlights: [
      'Curated harmony color systems',
      'Ultra-sharp vector illustrations',
      'Ready-to-use theme resource bundles',
      'Multi-format design source files'
    ]
  },
  {
    title: 'Nebula Programmatic Art Pack',
    description: 'A package of high-fidelity futuristic abstract graphics, generative art structures, and vector backdrops tailored for developer landing pages.',
    techs: ['Illustrator', 'AI Generation', 'Microstock'],
    highlights: [
      'High-resolution abstract canvases',
      'Programmatically scaled vector nodes',
      'Featured on multiple tech publications',
      'Optimized lightweight vector files'
    ]
  }
]
</script>

<template>
  <section id="projects" class="py-24 relative overflow-hidden bg-neutral-950/20 border-t border-white/5">
    <div class="max-w-7xl mx-auto px-6 relative z-10">
      
      <!-- Section Header & Tab Controls -->
      <div class="flex flex-col md:flex-row md:items-end justify-between gap-8 mb-16 text-left">
        
        <!-- Left: Text -->
        <div class="flex flex-col gap-4 max-w-xl">
          <span class="text-xs font-mono font-semibold uppercase tracking-widest text-neutral-500 font-mono">Product Showcase</span>
          <h2 class="text-3xl sm:text-4xl font-bold tracking-tight text-white leading-tight">
            Engineered Works
          </h2>
          <div class="h-1 w-12 bg-gradient-to-r from-brand-blue to-brand-cyan rounded-full"></div>
        </div>

        <!-- Right: Tab Switchers -->
        <div class="flex items-center gap-1 p-1 bg-neutral-900 border border-white/5 rounded-xl self-start md:self-auto">
          <button
            @click="activeTab = 'software'"
            :class="[
              'px-4 py-2 rounded-lg text-xs font-semibold tracking-wider uppercase transition-all duration-200 flex items-center gap-2 font-mono',
              activeTab === 'software'
                ? 'bg-brand-blue text-white shadow'
                : 'text-neutral-400 hover:text-white'
            ]"
          >
            <Terminal class="w-4 h-4" />
            <span>Software Engineer</span>
          </button>
          
          <button
            @click="activeTab = 'design'"
            :class="[
              'px-4 py-2 rounded-lg text-xs font-semibold tracking-wider uppercase transition-all duration-200 flex items-center gap-2 font-mono',
              activeTab === 'design'
                ? 'bg-brand-cyan text-white shadow'
                : 'text-neutral-400 hover:text-white'
            ]"
          >
            <Paintbrush class="w-4 h-4" />
            <span>Graphic Design</span>
          </button>
        </div>

      </div>

      <!-- Project Cards Grid -->
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
        
        <!-- Software engineering cards -->
        <template v-if="activeTab === 'software'">
          <div 
            v-for="project in softwareProjects" 
            :key="project.title"
            class="h-full"
          >
            <GlowCard>
              <div class="flex flex-col h-full justify-between text-left gap-6">
                <!-- Header & Description -->
                <div>
                  <div class="flex items-start justify-between gap-4 mb-4">
                    <h3 class="text-lg font-bold text-white tracking-tight leading-snug group-hover:text-brand-cyan transition-colors">
                      {{ project.title }}
                    </h3>
                    <div class="w-7 h-7 rounded-lg bg-neutral-850 border border-white/5 flex items-center justify-center text-neutral-400 group-hover:text-white group-hover:border-brand-cyan/20 transition-all flex-shrink-0">
                      <ArrowUpRight class="w-4 h-4" />
                    </div>
                  </div>
                  <p class="text-neutral-400 text-xs leading-relaxed mb-6">
                    {{ project.description }}
                  </p>

                  <!-- Tech Badges -->
                  <div class="flex flex-wrap gap-2 mb-6">
                    <span 
                      v-for="tech in project.techs" 
                      :key="tech"
                      class="px-2.5 py-1 rounded bg-neutral-950 border border-white/5 text-[10px] font-mono text-brand-cyan uppercase tracking-wider"
                    >
                      {{ tech }}
                    </span>
                  </div>
                </div>

                <!-- Highlights Checklist -->
                <div class="border-t border-white/5 pt-4">
                  <span class="text-[10px] font-mono text-neutral-500 uppercase tracking-widest block mb-3">Key Highlights:</span>
                  <div class="grid grid-cols-1 sm:grid-cols-2 gap-2.5">
                    <div 
                      v-for="hl in project.highlights" 
                      :key="hl"
                      class="flex items-start gap-2 text-[11px] text-neutral-400 leading-tight"
                    >
                      <CheckCircle2 class="w-3.5 h-3.5 text-brand-cyan flex-shrink-0 mt-0.5" />
                      <span>{{ hl }}</span>
                    </div>
                  </div>
                </div>
              </div>
            </GlowCard>
          </div>
        </template>

        <!-- Graphic design cards -->
        <template v-else>
          <div 
            v-for="project in designProjects" 
            :key="project.title"
            class="h-full"
          >
            <GlowCard>
              <div class="flex flex-col h-full justify-between text-left gap-6">
                <!-- Header & Description -->
                <div>
                  <div class="flex items-start justify-between gap-4 mb-4">
                    <h3 class="text-lg font-bold text-white tracking-tight leading-snug group-hover:text-brand-cyan transition-colors">
                      {{ project.title }}
                    </h3>
                    <div class="w-7 h-7 rounded-lg bg-neutral-850 border border-white/5 flex items-center justify-center text-neutral-400 group-hover:text-white group-hover:border-brand-cyan/20 transition-all flex-shrink-0">
                      <ArrowUpRight class="w-4 h-4" />
                    </div>
                  </div>
                  <p class="text-neutral-400 text-xs leading-relaxed mb-6">
                    {{ project.description }}
                  </p>

                  <!-- Tech Badges -->
                  <div class="flex flex-wrap gap-2 mb-6">
                    <span 
                      v-for="tech in project.techs" 
                      :key="tech"
                      class="px-2.5 py-1 rounded bg-neutral-950 border border-white/5 text-[10px] font-mono text-brand-cyan uppercase tracking-wider"
                    >
                      {{ tech }}
                    </span>
                  </div>
                </div>

                <!-- Highlights Checklist -->
                <div class="border-t border-white/5 pt-4">
                  <span class="text-[10px] font-mono text-neutral-500 uppercase tracking-widest block mb-3">Key Highlights:</span>
                  <div class="flex flex-col gap-2.5">
                    <div 
                      v-for="hl in project.highlights" 
                      :key="hl"
                      class="flex items-start gap-2 text-[11px] text-neutral-400 leading-tight"
                    >
                      <CheckCircle2 class="w-3.5 h-3.5 text-brand-cyan flex-shrink-0 mt-0.5" />
                      <span>{{ hl }}</span>
                    </div>
                  </div>
                </div>
              </div>
            </GlowCard>
          </div>
        </template>

      </div>

    </div>
  </section>
</template>
