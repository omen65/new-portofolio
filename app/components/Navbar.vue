<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { Menu, X, Code2, Cpu } from '@lucide/vue'

const isScrolled = ref(false)
const isMobileMenuOpen = ref(false)
const activeSection = ref('home')

const navItems = [
  { name: 'Home', href: '#home', id: 'home' },
  { name: 'About', href: '#about', id: 'about' },
  { name: 'Experience', href: '#experience', id: 'experience' },
  { name: 'Tech Stack', href: '#tech-stack', id: 'tech-stack' },
  { name: 'Projects', href: '#projects', id: 'projects' },
  { name: 'Contact', href: '#contact', id: 'contact' }
]

const handleScroll = () => {
  isScrolled.value = window.scrollY > 20

  // Determine active section based on scroll position
  const scrollPosition = window.scrollY + 100
  for (const item of navItems) {
    const el = document.getElementById(item.id)
    if (el) {
      const top = el.offsetTop
      const height = el.offsetHeight
      if (scrollPosition >= top && scrollPosition < top + height) {
        activeSection.value = item.id
      }
    }
  }
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
  handleScroll()
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const selectNavItem = (id) => {
  activeSection.value = id
  isMobileMenuOpen.value = false
}
</script>

<template>
  <nav
    :class="[
      'fixed top-0 left-0 right-0 z-50 transition-all duration-300 border-b',
      isScrolled 
        ? 'bg-neutral-950/80 backdrop-blur-md border-white/5 py-3' 
        : 'bg-transparent border-transparent py-5'
    ]"
  >
    <div class="max-w-7xl mx-auto px-6 flex items-center justify-between">
      <!-- Logo -->
      <a href="#home" class="flex items-center gap-2 group" @click="selectNavItem('home')">
        <img src="/my-icon.png" alt="icon" class="w-10 h-10" />
        <div>
          <span class="font-bold tracking-tight text-white block leading-none">Feri Anggriawan</span>
          <span class="text-[10px] text-neutral-500 font-mono tracking-widest uppercase mt-0.5 block">Enterprise Systems Engineer</span>
        </div>
      </a>

      <!-- Desktop Nav Menu -->
      <div class="hidden md:flex items-center gap-1 bg-neutral-900/60 border border-white/5 px-2 py-1.5 rounded-full backdrop-blur-lg">
        <a
          v-for="item in navItems"
          :key="item.id"
          :href="item.href"
          @click="selectNavItem(item.id)"
          :class="[
            'px-4 py-1.5 rounded-full text-xs font-medium tracking-wide transition-all duration-200',
            activeSection === item.id 
              ? 'bg-white/10 text-white shadow-sm' 
              : 'text-neutral-400 hover:text-white'
          ]"
        >
          {{ item.name }}
        </a>
      </div>

      <!-- Action Button (Hire Me) -->
      <div class="hidden md:flex items-center">
        <a
          href="#contact"
          @click="selectNavItem('contact')"
          class="relative group overflow-hidden px-4 py-2 rounded-lg bg-white text-black font-semibold text-xs transition-all hover:bg-neutral-100 hover:shadow-[0_0_15px_rgba(255,255,255,0.15)] flex items-center gap-1.5"
        >
          <Cpu class="w-3.5 h-3.5 transition-transform group-hover:rotate-45" />
          <span>Discuss Projects</span>
        </a>
      </div>

      <!-- Mobile Hamburger Button -->
      <button 
        class="md:hidden p-2 rounded-lg border border-white/10 bg-neutral-900/60 text-neutral-400 hover:text-white transition-colors"
        @click="toggleMobileMenu"
        aria-label="Toggle menu"
      >
        <Menu v-if="!isMobileMenuOpen" class="w-5 h-5" />
        <X v-else class="w-5 h-5" />
      </button>
    </div>

    <!-- Mobile Navigation Drawer -->
    <div
      v-if="isMobileMenuOpen"
      class="md:hidden absolute top-full left-0 right-0 bg-neutral-950/95 border-b border-white/5 backdrop-blur-lg transition-all"
    >
      <div class="px-6 py-4 flex flex-col gap-4">
        <a
          v-for="item in navItems"
          :key="item.id"
          :href="item.href"
          @click="selectNavItem(item.id)"
          :class="[
            'text-sm font-semibold tracking-wide py-2 border-b border-white/5 transition-all',
            activeSection === item.id 
              ? 'text-brand-cyan pl-2' 
              : 'text-neutral-400 hover:text-white pl-0'
          ]"
        >
          {{ item.name }}
        </a>
        <a
          href="#contact"
          @click="selectNavItem('contact')"
          class="w-full text-center py-2.5 rounded-lg bg-neutral-900 border border-white/10 hover:border-brand-cyan/30 text-white font-medium text-xs tracking-wider transition-colors mt-2"
        >
          Let's Collaborate
        </a>
      </div>
    </div>
  </nav>
</template>
