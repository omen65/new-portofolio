<script setup>
import { Terminal as TerminalIcon, Sparkles, FolderGit2, Mail } from '@lucide/vue'
</script>

<template>
  <section
    id="home"
    class="relative min-h-screen pt-32 pb-20 flex items-center justify-center bg-grid-pattern overflow-hidden"
  >
    <!-- Radial mesh glows for depth -->
    <div class="absolute inset-0 mesh-glow-1 pointer-events-none"></div>
    <div class="absolute inset-0 mesh-glow-2 pointer-events-none"></div>

    <div class="max-w-7xl mx-auto px-6 grid grid-cols-1 lg:grid-cols-12 gap-16 items-center relative z-10 w-full">
      <!-- Left Column: Copy & Presentation -->
      <div class="lg:col-span-7 flex flex-col items-start gap-6 text-left">
        
        <!-- Badge -->
        <div class="inline-flex items-center gap-2 px-3 py-1.5 rounded-full bg-brand-blue/10 border border-brand-blue/35 text-brand-blue text-[11px] font-semibold tracking-wider font-mono uppercase animate-pulse-slow">
          <Sparkles class="w-3 h-3 text-brand-cyan" />
          <span>Open to Freelance &amp; SaaS Collaboration</span>
        </div>

        <!-- Headline -->
        <h1 class="text-4xl sm:text-5xl lg:text-6xl font-bold tracking-tight leading-[1.08] text-white">
          Building <span class="text-cyan-blue-gradient">Real Products</span> <br />
          for <span class="text-glow-gradient">Real Problems</span>
        </h1>

        <!-- Subheadline -->
        <p class="text-neutral-400 text-sm sm:text-base lg:text-lg max-w-xl leading-relaxed">
          I'm a fullstack engineer with <span class="text-white font-medium">10 years of experience</span> focused on building multi-tenant SaaS, internal automation pipelines, robust backend architectures, and high-quality creative designs.
        </p>

        <!-- CTA Buttons -->
        <div class="flex flex-col sm:flex-row items-center gap-4 w-full sm:w-auto mt-4">
          <a
            href="#projects"
            class="relative w-full sm:w-auto px-6 py-3 rounded-lg bg-white text-black font-semibold text-xs transition-all hover:bg-neutral-100 hover:shadow-[0_0_20px_rgba(255,255,255,0.2)] flex items-center justify-center gap-2 group"
          >
            <FolderGit2 class="w-4 h-4 transition-transform group-hover:-translate-y-0.5" />
            <span>View Projects</span>
          </a>
          <a
            href="#contact"
            class="w-full sm:w-auto px-6 py-3 rounded-lg bg-neutral-900 border border-white/10 text-white font-semibold text-xs transition-all hover:border-white/20 hover:bg-neutral-900/60 flex items-center justify-center gap-2"
          >
            <Mail class="w-4 h-4 text-neutral-400" />
            <span>Contact Me</span>
          </a>
        </div>

        <!-- Quick Stats -->
        <div class="grid grid-cols-3 gap-8 border-t border-white/5 mt-10 pt-8 w-full font-mono">
          <div>
            <span class="block text-xl sm:text-2xl font-bold text-white tracking-tight">10+</span>
            <span class="text-[10px] text-neutral-500 uppercase tracking-widest">Years Exp</span>
          </div>
          <div>
            <span class="block text-xl sm:text-2xl font-bold text-white tracking-tight">100%</span>
            <span class="text-[10px] text-neutral-500 uppercase tracking-widest">Real Systems</span>
          </div>
          <div>
            <span class="block text-xl sm:text-2xl font-bold text-white tracking-tight">15k+</span>
            <span class="text-[10px] text-neutral-500 uppercase tracking-widest">Visual Assets</span>
          </div>
        </div>

      </div>

      <!-- Right Column: Interactive Terminal -->
      <div class="lg:col-span-5 flex items-center justify-center w-full animate-float">
        <Terminal />
      </div>
    </div>
  </section>
</template>
