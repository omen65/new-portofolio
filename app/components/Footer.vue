<script setup>
import { MessageCircle, Mail, ArrowUp } from '@lucide/vue'

const currentYear = new Date().getFullYear()

const socialLinks = [
  { name: 'GitHub', href: 'https://github.com', color: 'hover:text-white hover:border-white/20' },
  { name: 'LinkedIn', href: 'https://linkedin.com', color: 'hover:text-brand-blue hover:border-brand-blue/20' },
  { name: 'Threads', href: 'https://threads.net', icon: MessageCircle, color: 'hover:text-brand-cyan hover:border-brand-cyan/20' },
  { name: 'Email', href: 'mailto:contact@ferianggriawan.com', icon: Mail, color: 'hover:text-brand-emerald hover:border-brand-emerald/20' }
]

const scrollToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: 'smooth'
  })
}
</script>

<template>
  <footer class="relative border-t border-white/5 bg-neutral-950 py-16 overflow-hidden">
    <!-- Glowing background inside footer -->
    <div class="absolute inset-x-0 bottom-0 h-80 mesh-glow-footer pointer-events-none"></div>

    <div class="max-w-7xl mx-auto px-6 relative z-10">
      <div class="grid grid-cols-1 md:grid-cols-3 gap-12 items-center md:items-start text-center md:text-left">
        
        <!-- Left Side: Brand Story -->
        <div class="flex flex-col gap-3">
          <div class="flex items-center justify-center md:justify-start gap-2">
            <span class="font-bold text-white tracking-tight text-lg">Feri Anggriawan</span>
            <span class="px-2 py-0.5 rounded text-[10px] font-mono bg-brand-blue/15 border border-brand-blue/30 text-brand-blue uppercase">Enterprise Systems Engineer</span>
          </div>
          <p class="text-neutral-400 text-sm max-w-sm">
            Senior software engineer with 9+ years of experience architecting and building scalable custom ERPs, internal tools, and enterprise operational platforms.
          </p>
        </div>

        <!-- Middle Side: Social Connections -->
        <div class="flex flex-col items-center gap-4">
          <span class="text-neutral-500 font-mono tracking-widest text-[10px] uppercase">Connect & Collaborate</span>
          <div class="flex items-center gap-3">
            <a
              v-for="social in socialLinks"
              :key="social.name"
              :href="social.href"
              target="_blank"
              rel="noopener noreferrer"
              :class="[
                'w-10 h-10 rounded-lg bg-neutral-900 border border-white/5 flex items-center justify-center text-neutral-400 transition-all duration-300',
                social.color
              ]"
              :aria-label="social.name"
            >
              <!-- GitHub SVG -->
              <svg v-if="social.name === 'GitHub'" class="w-4 h-4" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M15 22v-4a4.8 4.8 0 0 0-1-3.5c3 0 6-2 6-5.5.08-1.25-.27-2.48-1-3.5.28-1.15.28-2.35 0-3.5 0 0-1 0-3 1.5-2.64-.5-5.36-.5-8 0C6 2 5 2 5 2c-.3 1.15-.3 2.35 0 3.5A5.403 5.403 0 0 0 4 9c0 3.5 3 5.5 6 5.5-.39.49-.68 1.05-.85 1.65-.17.6-.22 1.23-.15 1.85v4"></path>
                <path d="M9 18c-4.51 2-5-2-7-2"></path>
              </svg>
              <!-- LinkedIn SVG -->
              <svg v-else-if="social.name === 'LinkedIn'" class="w-4 h-4" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"></path>
                <rect x="2" y="9" width="4" height="12"></rect>
                <circle cx="4" cy="4" r="2"></circle>
              </svg>
              <!-- Lucide component for others -->
              <component v-else :is="social.icon" class="w-4 h-4" />
            </a>
          </div>
        </div>

        <!-- Right Side: Navigation & Scroll-to-Top -->
        <div class="flex flex-col items-center md:items-end justify-between h-full gap-6">
          <button 
            @click="scrollToTop"
            class="group w-10 h-10 rounded-lg bg-neutral-900 border border-white/5 flex items-center justify-center text-neutral-400 hover:text-white hover:border-brand-cyan/20 hover:shadow-[0_0_15px_rgba(6,182,212,0.15)] transition-all duration-300"
            aria-label="Scroll to top"
          >
            <ArrowUp class="w-4 h-4 transition-transform group-hover:-translate-y-0.5" />
          </button>
          
          <div class="text-xs text-neutral-500 font-mono">
            &copy; {{ currentYear }} Feri Anggriawan. All rights reserved.
          </div>
        </div>

      </div>

      <!-- Tech stack credits line -->
      <!-- <div class="border-t border-white/5 mt-12 pt-6 flex flex-col md:flex-row items-center justify-between text-xs text-neutral-600 gap-4">
        <p>Crafted from scratch with Nuxt 3, Vue, and Tailwind CSS.</p>
        <p class="font-mono text-[10px]">VER. 2026.1 // INFRASTRUCTURE READY</p>
      </div> -->
    </div>
  </footer>
</template>
