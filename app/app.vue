<script setup>
import { useHead } from '#imports'

useHead({
  title: 'Feri Anggriawan | Senior Fullstack Engineer & Indie Builder',
  meta: [
    { name: 'description', content: 'Software engineer with 10 years of experience building scalable business systems, web applications, multi-tenant SaaS, and digital products.' },
    { name: 'keywords', content: 'Feri Anggriawan, Fullstack Engineer, Software Engineer, Laravel, VueJS, NuxtJS, Node.js, SaaS Builder, Indie Hacker, Web Developer' },
    { property: 'og:title', content: 'Feri Anggriawan | Senior Fullstack Engineer & Indie Builder' },
    { property: 'og:description', content: 'Software engineer with 10 years of experience building scalable business systems, web applications, multi-tenant SaaS, and digital products.' },
    { property: 'og:type', content: 'website' }
  ],
  link: [
    { rel: 'icon', type: 'image/ico', href: '/favicon.ico' },
    { rel: 'preconnect', href: 'https://fonts.googleapis.com' },
    { rel: 'preconnect', href: 'https://fonts.gstatic.com', crossorigin: 'anonymous' },
    { rel: 'stylesheet', href: 'https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700;800&family=Fira+Code:wght@400;500;600&display=swap' }
  ]
})
</script>

<template>
  <div class="bg-bg-dark text-text-primary min-h-screen relative font-sans antialiased selection:bg-brand-cyan/20 selection:text-white">
    <!-- Floating Background Mesh Elements -->
    <div class="fixed inset-0 bg-grid-pattern opacity-60 pointer-events-none z-0"></div>
    <div class="fixed inset-x-0 top-0 h-[600px] mesh-glow-1 pointer-events-none z-0"></div>
    <div class="fixed inset-x-0 bottom-0 h-[600px] mesh-glow-footer pointer-events-none z-0"></div>

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
