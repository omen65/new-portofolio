<script setup>
import { ref } from 'vue'
import { Terminal, Paintbrush, ArrowUpRight, CheckCircle2 } from '@lucide/vue'

const activeTab = ref('software')

const softwareProjects = [
  {
    title: 'Custom ERP Ecosystem',
    description: 'A comprehensive custom Enterprise Resource Planning system tailored for manufacturing and distribution. Manages inventory, sales, and complex business logic.',
    techs: ['Laravel', 'Vue.js', 'MySQL', 'Docker'],
    highlights: [
      'Module-based architecture',
      'Complex requirements analysis',
      'Automated business logic',
      'Extensive user training & support',
      'Containerized deployments'
    ]
  },
  {
    title: 'Internal Operations Mobile App',
    description: 'A mobile application designed to support company operations and integrate seamlessly with existing ERP backend services.',
    techs: ['Mobile Dev', 'REST API', 'Security'],
    highlights: [
      'ERP data integration',
      'Performance & UX optimization',
      'Secure company data handling',
      'Real-time operational sync'
    ]
  },
  {
    title: 'B2B Enterprise Portals',
    description: 'A suite of web-based company information systems including customer portals, supplier registrations, and visitor management systems.',
    techs: ['PHP', 'JavaScript', 'MySQL'],
    highlights: [
      'Customer & Supplier Portals',
      'Visitor Management System',
      'Automated registration workflows',
      'Centralized data aggregation'
    ]
  },
  {
    title: 'Specialized Operational Platforms',
    description: 'Various custom business applications tailored for specific workflows, including POS systems, clinic management, and laboratory automation.',
    techs: ['Vue.js', 'Node.js', 'Laravel'],
    highlights: [
      'Point of Sale (POS) Systems',
      'Midwife Clinic Applications',
      'Laboratory Management Apps',
      'Process automation'
    ]
  }
]

const designProjects = [
  {
    title: 'Midwife Clinic System',
    description: 'A dedicated application to manage patient records, maternity scheduling, and operational billing for midwife clinics.',
    techs: ['Vue.js', 'Laravel', 'MySQL'],
    highlights: [
      'Patient health records tracking',
      'Appointment & schedule management',
      'Integrated billing & invoicing',
      'Secure data privacy controls'
    ]
  },
  {
    title: 'POS & Retail Systems',
    description: 'Custom Point of Sale solutions tailored for small and medium businesses to manage sales, stock, and daily transactions seamlessly.',
    techs: ['Vue.js', 'Tailwind', 'PHP'],
    highlights: [
      'Real-time transaction processing',
      'Daily sales reporting',
      'Inventory synchronization',
      'User-friendly cashier interface'
    ]
  },
  {
    title: 'Company Profile & Web Presence',
    description: 'High-quality, responsive company profile websites designed to establish a strong digital presence and showcase business services.',
    techs: ['Nuxt.js', 'Tailwind', 'Vite'],
    highlights: [
      'Modern aesthetics & animations',
      'SEO optimized structures',
      'Fast loading performance',
      'Custom content management'
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
          <span class="text-xs font-mono font-semibold uppercase tracking-widest text-neutral-500 font-mono">Systems Showcase</span>
          <h2 class="text-3xl sm:text-4xl font-bold tracking-tight text-white leading-tight">
            Engineered Platforms
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
            <span>Enterprise Systems</span>
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
            <Terminal class="w-4 h-4" />
            <span>Business Portals</span>
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
