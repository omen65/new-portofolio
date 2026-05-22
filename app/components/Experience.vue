<script setup>
import { Briefcase, Milestone, Sparkles, Paintbrush } from '@lucide/vue'

const experiences = [
  {
    role: 'Senior Software Engineer (Assistant Manager)',
    company: 'Van Aroma',
    period: 'Mar 2024 - Present',
    type: 'Full-time',
    description: 'Leading enterprise software architecture and development of custom ERP modules and internal mobile applications to drive core business operations.',
    achievements: [
      'Architected scalable enhancements for Custom ERP systems based on complex operational requirements.',
      'Engineered secure internal Mobile Applications with seamless integration to legacy ERP backend services.',
      'Spearheaded the development of scalable customer and supplier portals to streamline B2B interactions.',
      'Managed production servers, deployments, Docker migrations, database configuration, and backend performance optimization for enterprise operational systems.',
      'Led technical strategy, conducted rigorous code reviews, and mentored engineering teams.'
    ],
    icon: Briefcase,
    accent: 'border-brand-cyan text-brand-cyan bg-brand-cyan/10'
  },
  {
    role: 'Full Stack Developer',
    company: 'Van Aroma',
    period: 'May 2018 - Mar 2024',
    type: 'Full-time',
    description: 'Engineered robust internal business platforms and digitized manual workflows to improve enterprise-wide efficiency.',
    achievements: [
      'Conducted deep system requirements analysis to implement new modules in the core ERP application.',
      'Maintained and optimized existing business modules to ensure high availability and data integrity.',
      'Developed centralized operational platforms including visitor management and B2B registration systems.',
      'Provided critical technical support, user training, and rapid resolution for production systems.'
    ],
    icon: Briefcase,
    accent: 'border-brand-blue text-brand-blue bg-brand-blue/10'
  },
  {
    role: 'Software Consultan & Developer ',
    company: 'Freelance & Independent Projects',
    period: '2019 - Present',
    type: 'Freelance / Contract',
    description: 'Providing end-to-end custom software development, web & mobile applications, and custom business tools tailored for diverse clients.',
    achievements: [
      'Architected and delivered custom operational platforms, web applications, and mobile solutions based on specific client workflows.',
      'Developed custom operational tools including specialized Point of Sale (POS) and clinic management platforms.',
      'Engineered specialized software systems such as laboratory automation and scheduling workflows.',
      'Managed full-lifecycle deployment and server setups using custom Linux and Docker infrastructure.'
    ],
    icon: Sparkles,
    accent: 'border-brand-purple text-brand-purple bg-brand-purple/10'
  },
  {
    role: 'Freelance Graphic Designer',
    company: 'Self-Employed & Microstock Agencies',
    period: '2017 - Present',
    type: 'Freelance',
    description: 'Creating high-quality visual designs, branding assets, and packaging layouts for global clients and digital microstock platforms.',
    achievements: [
      'Designed logos, branding identities, product packaging, banners, and other visual assets for global clients.',
      'Contributed 5,000+ vector and design assets to microstock platforms, securing over 10,000+ downloads globally.'
    ],
    icon: Paintbrush,
    accent: 'border-amber-500 text-amber-500 bg-amber-500/10'
  }
]
</script>

<template>
  <section id="experience" class="py-24 relative overflow-hidden bg-neutral-950/40 border-t border-white/5">
    <div class="max-w-5xl mx-auto px-6 relative z-10">
      
      <!-- Section Header -->
      <div class="flex flex-col items-center text-center gap-4 mb-20 max-w-xl mx-auto">
        <span class="text-xs font-mono font-semibold uppercase tracking-widest text-neutral-500 font-mono">Professional Path</span>
        <h2 class="text-3xl sm:text-4xl font-bold tracking-tight text-white leading-tight">
          9 Years of Engineering Value
        </h2>
        <div class="h-1 w-12 bg-gradient-to-r from-brand-cyan to-brand-emerald rounded-full"></div>
      </div>

      <!-- Experience Timeline Grid -->
      <div class="relative pl-6 md:pl-0 border-l border-white/5 md:border-l-0 md:before:absolute md:before:inset-y-0 md:before:left-1/2 md:before:-ml-px md:before:w-0.5 md:before:bg-white/5 flex flex-col gap-16">
        
        <div 
          v-for="(exp, index) in experiences" 
          :key="exp.role" 
          class="relative flex flex-col md:grid md:grid-cols-2 md:gap-12 md:items-start group"
        >
          
          <!-- Timeline Marker Circle (Centered in desktop, left in mobile) -->
          <div class="absolute -left-[31px] md:left-1/2 md:-translate-x-1/2 top-1.5 z-20">
            <div :class="['w-12 h-12 rounded-xl border flex items-center justify-center shadow-lg transition-transform duration-300 group-hover:scale-110', exp.accent]">
              <component :is="exp.icon" class="w-5.5 h-5.5" />
            </div>
          </div>

          <!-- Position card (swaps columns on alternate nodes on desktop) -->
          <div 
            :class="[
              'md:flex md:flex-col text-left',
              index % 2 === 0 ? 'md:order-1 md:pr-12' : 'md:order-2 md:pl-12 md:col-start-2'
            ]"
          >
            <div class="glass-panel rounded-xl p-6 transition-all duration-300 border-white/5 hover:border-white/10 relative">
              <!-- Period badge -->
              <div class="flex flex-wrap items-center justify-between gap-3 mb-4">
                <span class="px-2.5 py-1 rounded bg-white/5 text-[10px] font-mono font-semibold text-brand-cyan tracking-wider uppercase">
                  {{ exp.period }}
                </span>
                <span class="text-[10px] text-neutral-500 font-mono tracking-widest uppercase">
                  {{ exp.type }}
                </span>
              </div>

              <h3 class="text-lg font-bold text-white tracking-tight">
                {{ exp.role }}
              </h3>
              <p class="text-brand-cyan text-xs font-mono mb-4">
                {{ exp.company }}
              </p>
              
              <p class="text-neutral-400 text-xs leading-relaxed mb-6">
                {{ exp.description }}
              </p>

              <!-- Achievements bullet points -->
              <div class="flex flex-col gap-3.5 border-t border-white/5 pt-4">
                <div 
                  v-for="achievement in exp.achievements" 
                  :key="achievement" 
                  class="flex items-start gap-2.5 text-[11px] text-neutral-400 leading-relaxed"
                >
                  <span class="w-1.5 h-1.5 rounded-full bg-brand-cyan/60 mt-1.5 flex-shrink-0"></span>
                  <span>{{ achievement }}</span>
                </div>
              </div>
            </div>
          </div>

          <!-- Timeline spacer label (shows the period in the opposite column in desktop) -->
          <div 
            :class="[
              'hidden md:flex md:flex-col justify-center items-center h-full pt-4',
              index % 2 === 0 ? 'md:order-2 md:pl-12 text-left items-start' : 'md:order-1 md:pr-12 text-right items-end'
            ]"
          >
            <span class="text-sm font-mono font-semibold text-neutral-500 group-hover:text-brand-cyan transition-colors">
              {{ exp.period }}
            </span>
            <span class="text-[10px] font-mono text-neutral-600 uppercase tracking-widest mt-1">
              {{ exp.type }}
            </span>
          </div>

        </div>

      </div>

    </div>
  </section>
</template>
