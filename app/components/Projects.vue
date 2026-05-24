<script setup>
import { ref } from 'vue'
import { Terminal, Paintbrush, ArrowUpRight, CheckCircle2, X } from '@lucide/vue'

const activeTab = ref('software')
const showModal = ref(false)

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
    title: 'ERP-Integrated Mobile Apps',
    description: 'A suite of custom mobile applications developed for both internal operations and external stakeholders (suppliers and customers), fully integrated with the core ERP system.',
    techs: ['Flutter', 'REST API', 'ERP Integration'],
    highlights: [
      'Internal Operational Tools',
      'External Supplier & Customer Apps',
      'Secure ERP backend integration',
      'Real-time synchronization'
    ]
  },
  {
    title: 'B2B Enterprise Portals',
    description: 'A suite of web portals linking external users with internal systems — from supplier registrations and visitor management to integrated company profile websites.',
    techs: ['Vue.js', 'PHP', 'MySQL'],
    highlights: [
      'Integrated Company Profile',
      'Customer & Supplier Portals',
      'Visitor Management System',
      'Real-time database sync'
    ]
  },
  {
    title: 'Infrastructure & DevOps',
    description: 'End-to-end server management and deployment infrastructure powering the entire enterprise ecosystem — from bare-metal to containerized environments.',
    techs: ['Docker', 'Linux', 'Nginx', 'CI/CD'],
    highlights: [
      'Bare-metal to Docker migration',
      'Zero-downtime deployments',
      'Server & performance tuning',
      'Multi-environment pipelines'
    ]
  }
]

const designProjects = [
  {
    title: 'Midwife Clinic System',
    description: 'A dedicated application to manage patient records, maternity scheduling, and operational billing for midwife clinics.',
    techs: ['Vue.js', 'Laravel', 'MySQL'],
    skeletonType: 'clinic',
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
    skeletonType: 'pos',
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
    skeletonType: 'web',
    highlights: [
      'Modern aesthetics & animations',
      'SEO optimized structures',
      'Fast loading performance',
      'Custom content management'
    ]
  },
  {
    title: 'Queue & Ticketing System',
    description: 'A real-time customer queue and ticket management platform designed to streamline service center flows.',
    techs: ['Vue.js', 'Node.js', 'Socket.io'],
    skeletonType: 'queue',
    highlights: [
      'Real-time ticket updates',
      'Multi-counter dashboard',
      'Automated voice recall',
      'Queue statistics & reporting'
    ]
  },
  {
    title: 'Laboratory Information Portal',
    description: 'Custom system for laboratory diagnostics, report scheduling, and secure result distribution.',
    techs: ['Laravel', 'Vue.js', 'PostgreSQL'],
    skeletonType: 'lab',
    highlights: [
      'Diagnostic report generation',
      'Patient schedule calendar',
      'Barcode integration',
      'Doctor & patient portals'
    ]
  },
  {
    title: 'E-Commerce & Warehouse Sync',
    description: 'B2C/B2B online storefront integrated directly with back-end inventory management and order fulfillment.',
    techs: ['Vue.js', 'Express', 'MySQL'],
    skeletonType: 'ecommerce',
    highlights: [
      'Live stock level syncing',
      'Integrated payment gateways',
      'Order fulfillment workflows',
      'Analytics & reporting dashboard'
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
            <Paintbrush class="w-4 h-4" />
            <span>Business Solutions</span>
          </button>
        </div>

      </div>

      <!-- Project Cards Grid -->
      <div class="flex flex-col gap-10">
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

          <!-- Business Solutions cards (Freelance) -->
          <template v-else>
            <div 
              v-for="project in designProjects.slice(0, 4)" 
              :key="project.title"
              class="h-full"
            >
              <GlowCard>
                <div class="flex flex-col h-full justify-between text-left gap-6">
                  <!-- Header & Description -->
                  <div>
                    <!-- Abstract CSS Mockup Preview -->
                    <div class="w-full h-32 rounded-lg border border-white/5 bg-neutral-950 overflow-hidden mb-5 relative flex items-center justify-center p-3 select-none">
                      <div class="absolute inset-0 bg-grid-pattern opacity-10"></div>
                      
                      <!-- Clinic Mockup -->
                      <div v-if="project.skeletonType === 'clinic'" class="w-full h-full flex flex-col gap-2 relative z-10 text-[9px] font-mono text-neutral-600">
                        <div class="flex items-center justify-between border-b border-white/5 pb-1">
                          <span class="text-white/80 font-bold">🏥 Clinic Portal</span>
                          <span class="text-brand-cyan px-1 rounded bg-brand-cyan/10">Active</span>
                        </div>
                        <div class="flex gap-2 flex-1">
                          <div class="flex-1 border border-white/5 rounded p-1.5 flex flex-col gap-1 bg-white/5">
                            <span class="text-[7px] text-neutral-400">PATIENTS</span>
                            <div class="h-1 bg-white/20 rounded w-3/4"></div>
                            <div class="h-1 bg-white/10 rounded w-1/2"></div>
                          </div>
                          <div class="w-16 border border-white/5 rounded p-1.5 flex flex-col gap-1 bg-white/5 justify-between">
                            <span class="text-[7px] text-neutral-400">APPOINTMENTS</span>
                            <span class="text-white text-xs font-bold font-sans">12</span>
                          </div>
                        </div>
                      </div>

                      <!-- POS Mockup -->
                      <div v-else-if="project.skeletonType === 'pos'" class="w-full h-full flex flex-col gap-2 relative z-10 text-[9px] font-mono text-neutral-600">
                        <div class="flex items-center justify-between border-b border-white/5 pb-1">
                          <span class="text-white/80 font-bold">🛒 POS Terminal</span>
                          <span class="text-neutral-400 font-sans">$4,820.00</span>
                        </div>
                        <div class="flex-1 flex items-end gap-1.5 px-2">
                          <div class="w-full bg-white/5 rounded-t h-8"></div>
                          <div class="w-full bg-brand-cyan/20 rounded-t h-12"></div>
                          <div class="w-full bg-white/5 rounded-t h-16"></div>
                          <div class="w-full bg-white/10 rounded-t h-10"></div>
                        </div>
                      </div>

                      <!-- Web Presence Mockup -->
                      <div v-else-if="project.skeletonType === 'web'" class="w-full h-full flex flex-col gap-1.5 relative z-10 text-[9px] font-mono text-neutral-600">
                        <div class="w-full h-5 rounded bg-white/5 border border-white/5 flex items-center px-1.5 justify-between">
                          <div class="flex gap-1">
                            <span class="w-1.5 h-1.5 rounded-full bg-rose-500/60"></span>
                            <span class="w-1.5 h-1.5 rounded-full bg-amber-500/60"></span>
                            <span class="w-1.5 h-1.5 rounded-full bg-emerald-500/60"></span>
                          </div>
                          <div class="h-1 bg-white/10 rounded w-12"></div>
                        </div>
                        <div class="flex-1 border border-white/5 rounded bg-white/5 p-2 flex flex-col justify-center items-center gap-1.5">
                          <span class="text-white font-bold text-[10px]">Premium Web Presence</span>
                          <div class="h-1 bg-white/10 rounded w-2/3"></div>
                        </div>
                      </div>

                      <!-- Queue Mockup -->
                      <div v-else-if="project.skeletonType === 'queue'" class="w-full h-full flex gap-2 relative z-10 text-[9px] font-mono text-neutral-600">
                        <div class="flex-1 border border-white/5 rounded p-2 flex flex-col justify-between bg-white/5">
                          <span class="text-[7px] text-neutral-400">NOW SERVING</span>
                          <span class="text-2xl font-bold text-white font-sans leading-none">A-42</span>
                        </div>
                        <div class="w-20 border border-white/5 rounded p-1.5 flex flex-col gap-1 bg-white/5">
                          <span class="text-[7px] text-neutral-400">COUNTERS</span>
                          <div class="flex justify-between text-[7px] text-neutral-400"><span class="text-white/80">C1</span> <span>A-41</span></div>
                          <div class="flex justify-between text-[7px] text-neutral-400"><span class="text-white/80">C2</span> <span>A-42</span></div>
                        </div>
                      </div>

                      <!-- Lab Mockup -->
                      <div v-else-if="project.skeletonType === 'lab'" class="w-full h-full flex flex-col gap-2 relative z-10 text-[9px] font-mono text-neutral-600">
                        <div class="flex items-center justify-between border-b border-white/5 pb-1">
                          <span class="text-white/80 font-bold">🧪 LIS Report Hub</span>
                          <span class="text-brand-purple px-1 rounded bg-brand-purple/10">Lab Sync</span>
                        </div>
                        <div class="flex-1 flex flex-col gap-1.5 justify-center">
                          <div class="flex items-center justify-between"><span class="text-white/85">Blood Test #1042</span> <span class="h-1 bg-brand-purple/40 w-8 rounded"></span></div>
                          <div class="flex items-center justify-between"><span class="text-white/85">Urinalysis #1043</span> <span class="h-1 bg-white/20 w-8 rounded"></span></div>
                        </div>
                      </div>

                      <!-- Ecommerce Mockup -->
                      <div v-else-if="project.skeletonType === 'ecommerce'" class="w-full h-full flex flex-col gap-2 relative z-10 text-[9px] font-mono text-neutral-600">
                        <div class="flex items-center justify-between border-b border-white/5 pb-1">
                          <span class="text-white/80 font-bold">📦 Warehouse Sync</span>
                          <span class="text-neutral-400">Live Stocks</span>
                        </div>
                        <div class="flex-1 flex gap-2 justify-between items-center">
                          <div class="flex-1 flex flex-col gap-1"><span class="text-[7px] text-neutral-400">API ORDER QUEUE</span> <div class="h-1.5 bg-brand-cyan/20 rounded w-full"></div></div>
                          <div class="h-7 w-7 rounded-full border border-dashed border-white/10 flex items-center justify-center"><div class="w-3 h-3 rounded-full bg-brand-cyan"></div></div>
                        </div>
                      </div>
                    </div>

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

        <!-- View All → opens modal -->
        <div v-if="activeTab === 'design'" class="flex justify-center mt-4">
          <button 
            @click="showModal = true"
            class="px-5 py-2.5 rounded-lg border border-white/5 hover:border-brand-cyan/30 bg-neutral-900/40 text-[11px] font-mono font-semibold uppercase tracking-wider text-neutral-400 hover:text-white transition-all duration-300 flex items-center gap-2 group"
          >
            <span>View All Projects</span>
            <ArrowUpRight class="w-3.5 h-3.5 transition-transform duration-300 group-hover:rotate-45" />
          </button>
        </div>
      </div>

    </div>
  </section>

  <!-- ===== Business Solutions Modal ===== -->
  <Teleport to="body">
    <Transition name="modal-fade">
      <div
        v-if="showModal"
        class="fixed inset-0 z-[100] flex items-end sm:items-center justify-center p-0 sm:p-6"
        @click.self="showModal = false"
      >
        <!-- Backdrop -->
        <div class="absolute inset-0 bg-neutral-950/85 backdrop-blur-sm" @click="showModal = false"></div>

        <!-- Panel -->
        <div class="modal-panel relative w-full sm:max-w-6xl max-h-[92vh] bg-neutral-900/95 border border-white/10 sm:rounded-2xl rounded-t-2xl overflow-hidden flex flex-col shadow-[0_0_80px_rgba(0,0,0,0.8)]">

          <!-- Modal Header -->
          <div class="flex items-center justify-between px-6 py-5 border-b border-white/5 flex-shrink-0 bg-neutral-950/60">
            <div class="flex items-center gap-3">
              <div class="w-8 h-8 rounded-lg bg-brand-cyan/10 border border-brand-cyan/20 flex items-center justify-center">
                <Paintbrush class="w-4 h-4 text-brand-cyan" />
              </div>
              <div>
                <span class="block text-[10px] font-mono text-neutral-500 uppercase tracking-widest">Freelance Portfolio</span>
                <h3 class="text-base font-bold text-white tracking-tight leading-none mt-0.5">Business Solutions</h3>
              </div>
              <span class="ml-1 px-2 py-0.5 rounded-full bg-brand-cyan/10 border border-brand-cyan/20 text-[10px] font-mono text-brand-cyan">{{ designProjects.length }} projects</span>
            </div>
            <button
              @click="showModal = false"
              class="w-9 h-9 rounded-lg border border-white/5 bg-neutral-900 hover:border-white/20 hover:bg-neutral-800 flex items-center justify-center text-neutral-400 hover:text-white transition-all duration-200"
            >
              <X class="w-4 h-4" />
            </button>
          </div>

          <!-- Scrollable Body -->
          <div class="overflow-y-auto p-6 flex-1">
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-5">
              <GlowCard v-for="project in designProjects" :key="project.title + '-modal'">
                <div class="flex flex-col h-full text-left gap-4">

                  <!-- Skeleton Mockup -->
                  <div class="w-full h-28 rounded-lg border border-white/5 bg-neutral-950 overflow-hidden relative flex items-center justify-center p-3 select-none flex-shrink-0">
                    <div class="absolute inset-0 bg-grid-pattern opacity-10"></div>
                    <div v-if="project.skeletonType === 'clinic'" class="w-full h-full flex flex-col gap-2 relative z-10 text-[9px] font-mono text-neutral-600">
                      <div class="flex items-center justify-between border-b border-white/5 pb-1"><span class="text-white/80 font-bold">🏥 Clinic Portal</span><span class="text-brand-cyan px-1 rounded bg-brand-cyan/10">Active</span></div>
                      <div class="flex gap-2 flex-1">
                        <div class="flex-1 border border-white/5 rounded p-1.5 flex flex-col gap-1 bg-white/5"><span class="text-[7px] text-neutral-400">PATIENTS</span><div class="h-1 bg-white/20 rounded w-3/4"></div><div class="h-1 bg-white/10 rounded w-1/2"></div></div>
                        <div class="w-16 border border-white/5 rounded p-1.5 flex flex-col gap-1 bg-white/5 justify-between"><span class="text-[7px] text-neutral-400">APPTS</span><span class="text-white text-xs font-bold font-sans">12</span></div>
                      </div>
                    </div>
                    <div v-else-if="project.skeletonType === 'pos'" class="w-full h-full flex flex-col gap-2 relative z-10 text-[9px] font-mono text-neutral-600">
                      <div class="flex items-center justify-between border-b border-white/5 pb-1"><span class="text-white/80 font-bold">🛒 POS Terminal</span><span class="text-neutral-400 font-sans">$4,820.00</span></div>
                      <div class="flex-1 flex items-end gap-1.5 px-2"><div class="w-full bg-white/5 rounded-t h-8"></div><div class="w-full bg-brand-cyan/20 rounded-t h-12"></div><div class="w-full bg-white/5 rounded-t h-16"></div><div class="w-full bg-white/10 rounded-t h-10"></div></div>
                    </div>
                    <div v-else-if="project.skeletonType === 'web'" class="w-full h-full flex flex-col gap-1.5 relative z-10 text-[9px] font-mono text-neutral-600">
                      <div class="w-full h-5 rounded bg-white/5 border border-white/5 flex items-center px-1.5 justify-between"><div class="flex gap-1"><span class="w-1.5 h-1.5 rounded-full bg-rose-500/60"></span><span class="w-1.5 h-1.5 rounded-full bg-amber-500/60"></span><span class="w-1.5 h-1.5 rounded-full bg-emerald-500/60"></span></div><div class="h-1 bg-white/10 rounded w-12"></div></div>
                      <div class="flex-1 border border-white/5 rounded bg-white/5 p-2 flex flex-col justify-center items-center gap-1.5"><span class="text-white font-bold text-[10px]">Premium Web Presence</span><div class="h-1 bg-white/10 rounded w-2/3"></div></div>
                    </div>
                    <div v-else-if="project.skeletonType === 'queue'" class="w-full h-full flex gap-2 relative z-10 text-[9px] font-mono text-neutral-600">
                      <div class="flex-1 border border-white/5 rounded p-2 flex flex-col justify-between bg-white/5"><span class="text-[7px] text-neutral-400">NOW SERVING</span><span class="text-2xl font-bold text-white font-sans leading-none">A-42</span></div>
                      <div class="w-20 border border-white/5 rounded p-1.5 flex flex-col gap-1 bg-white/5"><span class="text-[7px] text-neutral-400">COUNTERS</span><div class="flex justify-between text-[7px] text-neutral-400"><span class="text-white/80">C1</span><span>A-41</span></div><div class="flex justify-between text-[7px] text-neutral-400"><span class="text-white/80">C2</span><span>A-42</span></div></div>
                    </div>
                    <div v-else-if="project.skeletonType === 'lab'" class="w-full h-full flex flex-col gap-2 relative z-10 text-[9px] font-mono text-neutral-600">
                      <div class="flex items-center justify-between border-b border-white/5 pb-1"><span class="text-white/80 font-bold">🧪 LIS Report Hub</span><span class="text-brand-purple px-1 rounded bg-brand-purple/10">Lab Sync</span></div>
                      <div class="flex-1 flex flex-col gap-1.5 justify-center"><div class="flex items-center justify-between"><span class="text-white/85">Blood Test #1042</span><span class="h-1 bg-brand-purple/40 w-8 rounded"></span></div><div class="flex items-center justify-between"><span class="text-white/85">Urinalysis #1043</span><span class="h-1 bg-white/20 w-8 rounded"></span></div></div>
                    </div>
                    <div v-else-if="project.skeletonType === 'ecommerce'" class="w-full h-full flex flex-col gap-2 relative z-10 text-[9px] font-mono text-neutral-600">
                      <div class="flex items-center justify-between border-b border-white/5 pb-1"><span class="text-white/80 font-bold">📦 Warehouse Sync</span><span class="text-neutral-400">Live Stocks</span></div>
                      <div class="flex-1 flex gap-2 justify-between items-center"><div class="flex-1 flex flex-col gap-1"><span class="text-[7px] text-neutral-400">API ORDER QUEUE</span><div class="h-1.5 bg-brand-cyan/20 rounded w-full"></div></div><div class="h-7 w-7 rounded-full border border-dashed border-white/10 flex items-center justify-center"><div class="w-3 h-3 rounded-full bg-brand-cyan"></div></div></div>
                    </div>
                  </div>

                  <!-- Info -->
                  <div>
                    <h4 class="text-sm font-bold text-white tracking-tight leading-snug group-hover:text-brand-cyan transition-colors mb-1.5">{{ project.title }}</h4>
                    <p class="text-neutral-500 text-[11px] leading-relaxed mb-3">{{ project.description }}</p>
                    <div class="flex flex-wrap gap-1.5">
                      <span v-for="tech in project.techs" :key="tech" class="px-2 py-0.5 rounded bg-neutral-950 border border-white/5 text-[9px] font-mono text-brand-cyan uppercase tracking-wider">{{ tech }}</span>
                    </div>
                  </div>

                  <!-- Highlights -->
                  <div class="border-t border-white/5 pt-3 mt-auto">
                    <div class="flex flex-col gap-1.5">
                      <div v-for="hl in project.highlights" :key="hl" class="flex items-start gap-1.5 text-[10px] text-neutral-400 leading-tight">
                        <CheckCircle2 class="w-3 h-3 text-brand-cyan flex-shrink-0 mt-0.5" />
                        <span>{{ hl }}</span>
                      </div>
                    </div>
                  </div>

                </div>
              </GlowCard>
            </div>
          </div>

          <!-- Modal Footer -->
          <div class="px-6 py-4 border-t border-white/5 bg-neutral-950/40 flex-shrink-0 flex items-center justify-between">
            <span class="text-[10px] font-mono text-neutral-600">{{ designProjects.length }} freelance projects total</span>
            <button
              @click="showModal = false"
              class="px-4 py-2 rounded-lg border border-white/5 hover:border-white/20 bg-neutral-900 text-xs font-mono font-semibold text-neutral-400 hover:text-white transition-all"
            >Close</button>
          </div>

        </div>
      </div>
    </Transition>
  </Teleport>

</template>

<style scoped>
.modal-fade-enter-active,
.modal-fade-leave-active {
  transition: opacity 0.25s ease;
}
.modal-fade-enter-from,
.modal-fade-leave-to {
  opacity: 0;
}
.modal-fade-enter-active .modal-panel {
  transition: transform 0.3s cubic-bezier(0.34, 1.56, 0.64, 1), opacity 0.3s ease;
}
.modal-fade-leave-active .modal-panel {
  transition: transform 0.2s ease, opacity 0.2s ease;
}
.modal-fade-enter-from .modal-panel,
.modal-fade-leave-to .modal-panel {
  transform: translateY(16px) scale(0.97);
  opacity: 0;
}
</style>
