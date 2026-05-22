<script setup>
import { useHead } from '#imports'

useHead({
  title: 'Feri Anggriawan | Software Engineer & Custom App Developer',
  meta: [
    { name: 'description', content: 'Software engineer with 9+ years of experience. Specializes in custom ERP systems, web & mobile applications, and business operational platforms — for any scale.' },
    { name: 'keywords', content: 'Feri Anggriawan, Custom Software Developer, ERP System, Web App, Mobile App, Laravel, Vue.js, Flutter, Nuxt.js, Node.js, POS System, Clinic App' },
    { property: 'og:title', content: 'Feri Anggriawan | Software Engineer & Custom App Developer' },
    { property: 'og:description', content: 'Software engineer with 9+ years experience building custom ERP, web & mobile apps, and business systems — enterprise quality for any project size.' },
    { property: 'og:type', content: 'website' }
  ],
  link: [
    { rel: 'icon', type: 'image/png', href: '/my-icon.png' },
    { rel: 'preconnect', href: 'https://fonts.googleapis.com' },
    { rel: 'preconnect', href: 'https://fonts.gstatic.com', crossorigin: 'anonymous' },
    { rel: 'stylesheet', href: 'https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700;800&family=Fira+Code:wght@400;500;600&display=swap' }
  ]
})
</script>

<template>
  <div class="bg-bg-dark text-text-primary min-h-screen relative font-sans antialiased selection:bg-brand-cyan/20 selection:text-white">
    <!-- Floating Background Mesh Elements -->
    <div class="fixed inset-0 bg-grid-pattern opacity-30 pointer-events-none z-0"></div>
    <div class="fixed inset-x-0 top-0 h-[600px] mesh-glow-1 opacity-50 pointer-events-none z-0"></div>
    <div class="fixed inset-x-0 bottom-0 h-[600px] mesh-glow-footer opacity-50 pointer-events-none z-0"></div>

    <!-- Core Layout Assembly -->
    <div class="relative z-10 flex flex-col min-h-screen">
      <Navbar />
      
      <main class="flex-grow">
        <Hero />
        <About />
        <Experience />
        <TechStack />
        <Projects />
        <Contact />
      </main>

      <Footer />
    </div>
  </div>
</template>
