<script setup>
import { ref } from 'vue'
import { Terminal, Paintbrush, ArrowUpRight, CheckCircle2, X, Sparkles } from '@lucide/vue'

const activeTab = ref('software')
const showModal = ref(false)

const softwareProjects = [
  {
    title: 'Custom ERP Ecosystem',
    description: 'Enterprise-grade ERP system engineered for manufacturing and distribution operations. Manages complex inventory flows, sales cycles, production scheduling, and cross-departmental workflows with real operational business logic.',
    techs: ['Code Igniter 4', 'MySQL', 'REST API','Automation Scripts','Web Sockets','API Integrations','Payment Gateway Integrations','Reporting & Analytics','Document Generation'],
    highlights: [
      'Scalable module-based architecture',
      'Deep requirements analysis & implementation',
      'Complex business logic automation',
      'Long-term maintenance & system evolution',
      'High availability & data integrity'
    ]
  },
  {
    title: 'ERP-Integrated Mobile Applications',
    description: 'Cross-platform mobile suite connecting field operations and external stakeholders directly to core ERP backend. Includes internal operational tools and dedicated apps for suppliers and customers with seamless data synchronization.',
    techs: ['Flutter', 'REST API','Firebase','Offline Sync','Mobile Security Best Practices'],
    highlights: [
      'Internal operational mobile tools',
      'External supplier & customer apps',
      'Secure legacy ERP integration',
      'Real-time bidirectional sync',
      'Offline-capable workflows'
    ]
  },
  {
    title: 'Web Platforms & B2B Portals',
    description: 'Comprehensive web ecosystem including customer/supplier portals, visitor management systems, and integrated corporate profile websites. Built to extend internal ERP capabilities to external stakeholders and establish strong digital presence.',
    techs: ['Vue.js', 'Nuxt.js','REST API'],
    highlights: [
      'Customer & supplier self-service portals',
      'Integrated corporate profile websites',
      'Visitor management & registration systems',
      'Subsidiary company platforms',
      'Real-time ERP database synchronization'
    ]
  },
  {
    title: 'Infrastructure & DevOps',
    description: 'Production-grade server infrastructure and deployment pipelines supporting the entire enterprise ecosystem. Managed complete migration from bare-metal to containerized environments with focus on performance optimization and zero-downtime deployments.',
    techs: ['Docker', 'Linux', 'Nginx', 'Git', 'PM2','CI/CD Pipelines','Server Monitoring','Performance Optimization','Security Hardening'],
    highlights: [
      'Bare-metal to Docker containerization',
      'Production server management',
      'Database configuration & optimization',
      'Zero-downtime deployment strategies',
      'Multi-environment infrastructure'
    ]
  }
]

const solutionsProjects = [
  {
    title: 'Goestowedding.com',
    description: 'Full-featured SAAS platform for digital wedding invitations with integrated payment gateway. Evolved from CodeIgniter to Laravel architecture, serving couples with customizable invitation templates, RSVP management, and guest tracking capabilities.',
    techs: ['Laravel', 'MySQL', 'Payment Gateway', 'SAAS Architecture'],
    skeletonType: 'web',
    coverImage: 'projects/goestowedding.webp',
    demoUrl: 'https://goestowedding.com',
    highlights: [
      'SAAS-based digital invitation platform',
      'Payment gateway integration',
      'Customizable invitation templates',
      'RSVP & guest management system',
      'Migrated from CodeIgniter to Laravel'
    ]
  },
  {
    title: 'Point APP',
    description: 'Enterprise-grade POS and inventory management system specifically engineered for F&B business operations. Currently deployed across 5 active branches with comprehensive transaction management, automated receipt printing, profit analytics, and real-time sales reporting.',
    techs: ['Laravel', 'Tailwind CSS', 'MySQL', 'Multi-Branch', 'Thermal Printer'],
    skeletonType: 'pos',
    coverImage: 'projects/point.webp',
    demoUrl: 'https://pointapp.id/',
    highlights: [
      'Full-featured POS/cashier system',
      'Automated receipt printing (thermal)',
      'Profit & loss reporting',
      'Real-time sales analytics',
      'Deployed across 5 active branches',
      'Real-time inventory tracking',
      'Multi-location data synchronization'
    ]
  },
  {
    title: 'Synta (Sistem Informasi Pasien Kita)',
    description: 'Comprehensive midwife clinic management system supporting 6 examination types: ANC (Antenatal Care), INC (Intranatal Care), PNC (Postnatal Care), Infant/Toddler Health, Family Planning, and General Examinations. Manages complete patient workflows from registration to payment.',
    techs: ['Laravel', 'Tailwind CSS', 'MySQL', 'PDF Generation'],
    skeletonType: 'clinic',
    coverImage: 'projects/synta.webp',
    demoUrl: null,
    highlights: [
      '6 specialized examination types (ANC, INC, PNC, KB, Bayi/Balita, Umum)',
      'Complete patient data management',
      'Digital medical records system',
      'Examination & financial reporting',
      'Automated payment receipt printing'
    ]
  },
  {
    title: 'LabDash',
    description: 'Comprehensive laboratory management system for a state university, integrating inventory control, staff scheduling, attendance tracking, document management, and digital questionnaire system. Streamlines laboratory operations and ensures regulatory compliance.',
    techs: ['Laravel', 'MySQL', 'Document Management', 'Questionnaire System'],
    skeletonType: 'lab',
    coverImage: 'projects/labdash.webp',
    demoUrl: null,
    highlights: [
      'University laboratory management',
      'Inventory & equipment tracking',
      'Staff scheduling & attendance',
      'Digital questionnaire & survey system',
      'Document management system',
      'Academic compliance features'
    ]
  },
  {
    title: 'SIMS (Sales & Inventory Management)',
    description: 'Filament-powered sales and inventory management platform designed for small and medium enterprises. Currently serving multiple UMKM businesses with real-time stock tracking, sales reporting, and business analytics.',
    techs: ['Laravel Filament', 'MySQL', 'Business Analytics'],
    skeletonType: 'ecommerce',
    coverImage: 'projects/sims.webp',
    demoUrl: null,
    highlights: [
      'Built with Laravel Filament framework',
      'Used by multiple UMKM clients',
      'Real-time inventory management',
      'Sales analytics & reporting',
      'Scalable multi-tenant architecture'
    ]
  },
  {
    title: 'Routify',
    description: 'Specialized logistics management application built for courier and delivery service providers. Features route optimization, delivery tracking, and operational workflow management powered by Laravel Filament.',
    techs: ['Laravel Filament', 'MySQL', 'Route Management'],
    skeletonType: 'queue',
    coverImage: 'projects/routify.webp',
    demoUrl: null,
    highlights: [
      'Logistics service provider platform',
      'Route planning & optimization',
      'Delivery tracking system',
      'Driver & fleet management',
      'Real-time operational dashboard'
    ]
  },
  {
    title: 'sahabat-ibu.id',
    description: 'Educational screening platform for mothers and children developed in collaboration with midwives and midwifery university. Features comprehensive 3-in-1 screening: Physical Anthropometry Monitoring, KPSP (Child Development Pre-Screening Questionnaire), and EPDS (Edinburgh Postnatal Depression Scale).',
    techs: ['Laravel Filament', 'MySQL', 'Health Screening'],
    skeletonType: 'clinic',
    coverImage: 'projects/sahabat_ibu.webp',
    demoUrl: 'https://sahabat-ibu.id',
    highlights: [
      '3-in-1 screening system (Anthropometry, KPSP, EPDS)',
      'Mother & child health monitoring',
      'Educational content platform',
      'University & midwife collaboration',
      'Evidence-based screening protocols'
    ]
  },
  {
    title: 'Additional Client Projects',
    description: 'Portfolio of diverse web solutions including company profile websites with CMS, e-commerce platforms with payment gateway integrations, and custom web applications. Built with modern tech stacks including Vue.js, Nuxt.js, Express.js, and Laravel tailored to client requirements.',
    techs: ['Vue.js', 'Nuxt.js', 'Express.js', 'Laravel', 'Various Stacks'],
    skeletonType: 'web',
    coverImage: null,
    demoUrl: null,
    highlights: [
      'Company profile websites with CMS',
      'E-commerce with payment gateways',
      'Custom web applications',
      'Modern frontend & backend stacks',
      'Client privacy maintained'
    ]
  }
]

const microstockProjects = [
  {
    title: 'Adobe Stock Portfolio',
    description: '5,000+ professional vector designs and graphic assets available for commercial licensing. Focused on modern illustrations, business graphics, and creative templates.',
    platform: 'Adobe Stock',
    url: 'https://stock.adobe.com/contributor/208257873/Feri%20Anggriawan',
    highlights: [
      'Premium vector illustrations',
      'Business & marketing templates',
      'Icon sets & UI elements',
      'Editorial & creative graphics'
    ]
  },
  {
    title: 'Shutterstock Collection',
    description: 'Extensive library of scalable vector graphics, illustrations, and design elements trusted by creative professionals worldwide.',
    platform: 'Shutterstock',
    url: 'https://www.shutterstock.com/g/omen65',
    highlights: [
      'High-quality vector graphics',
      'Commercial-use ready assets',
      'Diverse illustration styles',
      'Trending design themes'
    ]
  },
  {
    title: 'Magnific (Freepik) Gallery',
    description: 'Curated collection of premium design resources, vectors, and creative assets for modern digital and print projects.',
    platform: 'Magnific',
    url: 'https://www.magnific.com/author/omen65',
    highlights: [
      'Premium design resources',
      'Modern vector collections',
      'Editorial & branding assets',
      'High-impact visual content'
    ]
  },
  {
    title: 'Vecteezy Contributions',
    description: 'Community-driven portfolio featuring free and premium vector resources for designers, marketers, and content creators.',
    platform: 'Vecteezy',
    url: 'https://www.vecteezy.com/members/113942821074662886116',
    highlights: [
      'Free & premium vectors',
      'Community-approved designs',
      'Versatile graphic elements',
      'Designer-friendly formats'
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
        <div class="flex items-center gap-1 p-1 bg-neutral-900 border border-white/5 rounded-xl self-start md:self-auto flex-wrap">
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
            <span>Enterprise</span>
          </button>
          
          <button
            @click="activeTab = 'freelance'"
            :class="[
              'px-4 py-2 rounded-lg text-xs font-semibold tracking-wider uppercase transition-all duration-200 flex items-center gap-2 font-mono',
              activeTab === 'freelance'
                ? 'bg-brand-cyan text-white shadow'
                : 'text-neutral-400 hover:text-white'
            ]"
          >
            <Paintbrush class="w-4 h-4" />
            <span>Solutions</span>
          </button>

          <button
            @click="activeTab = 'design'"
            :class="[
              'px-4 py-2 rounded-lg text-xs font-semibold tracking-wider uppercase transition-all duration-200 flex items-center gap-2 font-mono',
              activeTab === 'design'
                ? 'bg-brand-purple text-white shadow'
                : 'text-neutral-400 hover:text-white'
            ]"
          >
            <Sparkles class="w-4 h-4" />
            <span>Design</span>
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
          <template v-else-if="activeTab === 'freelance'">
            <div 
              v-for="project in solutionsProjects.slice(0, 4)" 
              :key="project.title"
              class="h-full"
            >
              <GlowCard>
                <div class="flex flex-col h-full justify-between text-left gap-6">
                  <!-- Header & Description -->
                  <div>
                    <!-- Cover Image or Abstract CSS Mockup Preview -->
                    <div class="w-full h-64 rounded-lg border border-white/5 bg-neutral-950 overflow-hidden mb-5 relative flex items-center justify-center p-3 select-none group/cover">
                      <!-- Real Cover Image if exists -->
                      <img 
                        v-if="project.coverImage" 
                        :src="`/${project.coverImage}`" 
                        :alt="project.title"
                        loading="lazy"
                        class="absolute inset-0 w-full h-full object-cover transition-transform duration-300 group-hover/cover:scale-105"
                      />
                      
                      <!-- Demo Link Overlay -->
                      <a
                        v-if="project.coverImage && project.demoUrl"
                        :href="project.demoUrl"
                        target="_blank"
                        rel="noopener noreferrer"
                        class="absolute inset-0 bg-black/60 opacity-0 hover:opacity-100 transition-opacity duration-300 flex items-center justify-center z-10"
                      >
                        <div class="flex items-center gap-2 px-4 py-2 rounded-lg bg-white/10 backdrop-blur-sm border border-white/20 text-white text-xs font-semibold">
                          <span>View Demo</span>
                          <ArrowUpRight class="w-3.5 h-3.5" />
                        </div>
                      </a>
                      
                      <!-- Skeleton Mockups - hanya muncul kalau tidak ada coverImage -->
                      <template v-if="!project.coverImage">
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
                      </template>
                    </div>

                    <div class="flex items-start justify-between gap-4 mb-4">
                      <h3 class="text-lg font-bold text-white tracking-tight leading-snug group-hover:text-brand-cyan transition-colors">
                        {{ project.title }}
                      </h3>
                      <a
                        v-if="project.demoUrl"
                        :href="project.demoUrl"
                        target="_blank"
                        rel="noopener noreferrer"
                        class="w-7 h-7 rounded-lg bg-neutral-850 border border-white/5 flex items-center justify-center text-neutral-400 hover:text-white hover:border-brand-cyan/20 transition-all flex-shrink-0"
                      >
                        <ArrowUpRight class="w-4 h-4" />
                      </a>
                      <div v-else class="w-7 h-7 rounded-lg bg-neutral-850 border border-white/5 flex items-center justify-center text-neutral-400 group-hover:text-white group-hover:border-brand-cyan/20 transition-all flex-shrink-0">
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

          <!-- Design Portfolio cards (Microstock) -->
          <template v-else-if="activeTab === 'design'">
            <div 
              v-for="project in microstockProjects" 
              :key="project.title"
              class="h-full"
            >
              <GlowCard>
                <div class="flex flex-col h-full justify-between text-left gap-6">
                  <!-- Header & Description -->
                  <div>
                    <div class="flex items-start justify-between gap-4 mb-4">
                      <div class="flex-1">
                        <div class="flex items-center gap-2 mb-2">
                          <Sparkles class="w-4 h-4 text-brand-purple" />
                          <span class="text-[10px] font-mono text-brand-purple uppercase tracking-wider">{{ project.platform }}</span>
                        </div>
                        <h3 class="text-lg font-bold text-white tracking-tight leading-snug group-hover:text-brand-purple transition-colors">
                          {{ project.title }}
                        </h3>
                      </div>
                    </div>
                    <p class="text-neutral-400 text-xs leading-relaxed mb-6">
                      {{ project.description }}
                    </p>
                  </div>

                  <!-- Highlights & Link -->
                  <div class="border-t border-white/5 pt-4">
                    <span class="text-[10px] font-mono text-neutral-500 uppercase tracking-widest block mb-3">Portfolio Highlights:</span>
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-2.5 mb-4">
                      <div 
                        v-for="hl in project.highlights" 
                        :key="hl"
                        class="flex items-start gap-2 text-[11px] text-neutral-400 leading-tight"
                      >
                        <CheckCircle2 class="w-3.5 h-3.5 text-brand-purple flex-shrink-0 mt-0.5" />
                        <span>{{ hl }}</span>
                      </div>
                    </div>
                    <a 
                      :href="project.url" 
                      target="_blank" 
                      rel="noopener noreferrer"
                      class="inline-flex items-center gap-2 px-4 py-2 rounded-lg bg-brand-purple/10 border border-brand-purple/20 hover:border-brand-purple/40 text-xs font-mono text-brand-purple hover:text-white transition-all group"
                    >
                      <span>View Portfolio</span>
                      <ArrowUpRight class="w-3.5 h-3.5 transition-transform group-hover:translate-x-0.5 group-hover:-translate-y-0.5" />
                    </a>
                  </div>
                </div>
              </GlowCard>
            </div>
          </template>

        </div>

        <!-- View All → opens modal (only for freelance tab) -->
        <div v-if="activeTab === 'freelance'" class="flex justify-center mt-4">
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
                <h3 class="text-base font-bold text-white tracking-tight leading-none mt-0.5">All Business Solutions</h3>
              </div>
              <span class="ml-1 px-2 py-0.5 rounded-full bg-brand-cyan/10 border border-brand-cyan/20 text-[10px] font-mono text-brand-cyan">{{ solutionsProjects.length }} projects</span>
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
              <GlowCard v-for="project in solutionsProjects" :key="project.title + '-modal'">
                <div class="flex flex-col h-full text-left gap-4">

                  <!-- Skeleton Mockup -->
                  <div class="w-full h-48 rounded-lg border border-white/5 bg-neutral-950 overflow-hidden relative flex items-center justify-center p-3 select-none flex-shrink-0 group/cover">
                    <!-- Real Cover Image if exists -->
                    <img 
                      v-if="project.coverImage" 
                      :src="`/${project.coverImage}`" 
                      :alt="project.title"
                      loading="lazy"
                      class="absolute inset-0 w-full h-full object-cover transition-transform duration-300 group-hover/cover:scale-105"
                    />
                    
                    <!-- Demo Link Overlay -->
                    <a
                      v-if="project.coverImage && project.demoUrl"
                      :href="project.demoUrl"
                      target="_blank"
                      rel="noopener noreferrer"
                      class="absolute inset-0 bg-black/60 opacity-0 hover:opacity-100 transition-opacity duration-300 flex items-center justify-center z-10"
                    >
                      <div class="flex items-center gap-2 px-3 py-1.5 rounded-lg bg-white/10 backdrop-blur-sm border border-white/20 text-white text-[10px] font-semibold">
                        <span>View Demo</span>
                        <ArrowUpRight class="w-3 h-3" />
                      </div>
                    </a>
                    
                    <!-- Skeleton Mockups - hanya muncul kalau tidak ada coverImage -->
                    <template v-if="!project.coverImage">
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
                    </template>
                  </div>

                  <!-- Info -->
                  <div>
                    <div class="flex items-start justify-between gap-3 mb-1.5">
                      <h4 class="text-sm font-bold text-white tracking-tight leading-snug group-hover:text-brand-cyan transition-colors flex-1">{{ project.title }}</h4>
                      <a
                        v-if="project.demoUrl"
                        :href="project.demoUrl"
                        target="_blank"
                        rel="noopener noreferrer"
                        class="w-6 h-6 rounded-lg bg-neutral-850 border border-white/5 flex items-center justify-center text-neutral-400 hover:text-white hover:border-brand-cyan/20 transition-all flex-shrink-0"
                      >
                        <ArrowUpRight class="w-3.5 h-3.5" />
                      </a>
                      <div v-else class="w-6 h-6 rounded-lg bg-neutral-850 border border-white/5 flex items-center justify-center text-neutral-400 group-hover:text-white group-hover:border-brand-cyan/20 transition-all flex-shrink-0">
                        <ArrowUpRight class="w-3.5 h-3.5" />
                      </div>
                    </div>
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
            <span class="text-[10px] font-mono text-neutral-600">{{ solutionsProjects.length }} freelance projects total</span>
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
