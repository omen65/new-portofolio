<script setup>
import { ref, onMounted, nextTick } from 'vue'
import { Terminal as TerminalIcon, Play, RefreshCw } from '@lucide/vue'

const inputCommand = ref('')
const terminalBody = ref(null)

const history = ref([
  { type: 'system', text: 'Feri Anggriawan System Shell v4.0.0 (ttyS001)' },
  { type: 'system', text: "Type 'help' or click the action shortcuts below." },
  { type: 'input', text: 'neofetch' },
  { 
    type: 'output', 
    text: `   .---.       \x1b[36mOS\x1b[0m: macOS Carbon / Linux Server
  /     \\      \x1b[36mRole\x1b[0m: Senior Fullstack Engineer
  \\     /      \x1b[36mExperience\x1b[0m: 10+ Years (Established 2016)
   '---'       \x1b[36mSpecialties\x1b[0m: Multi-tenant SaaS, Business Tools, High Performance APIs
               \x1b[36mFrontend\x1b[0m: Vue.js, Nuxt.js, React, Tailwind CSS
               \x1b[36mBackend\x1b[0m: Node.js, Laravel (PHP), Express
               \x1b[36mInfra\x1b[0m: Docker, Nginx, Linux, PM2, MySQL` 
  }
])

const shortcuts = ['about', 'skills', 'projects', 'neofetch', 'clear']

const executeCommand = (commandText) => {
  const cmd = commandText.trim().toLowerCase()
  if (!cmd) return

  history.value.push({ type: 'input', text: commandText })

  let outputText = ''
  switch (cmd) {
    case 'help':
      outputText = `Available commands:
  - \x1b[36mneofetch\x1b[0m : Display general profile overview & tech specs.
  - \x1b[36mabout\x1b[0m    : Read about Feri's software engineering ethos.
  - \x1b[36mskills\x1b[0m   : Inspect detailed tech stack.
  - \x1b[36mprojects\x1b[0m : List key projects in Feri's portfolio.
  - \x1b[36mclear\x1b[0m    : Clear the terminal history.`
      break
    case 'neofetch':
      outputText = `   .---.       \x1b[36mOS\x1b[0m: macOS Carbon / Linux Server
  /     \\      \x1b[36mRole\x1b[0m: Senior Fullstack Engineer
  \\     /      \x1b[36mExperience\x1b[0m: 10+ Years (Established 2016)
   '---'       \x1b[36mSpecialties\x1b[0m: Multi-tenant SaaS, Business Tools, High Performance APIs
               \x1b[36mFrontend\x1b[0m: Vue.js, Nuxt.js, React, Tailwind CSS
               \x1b[36mBackend\x1b[0m: Node.js, Laravel (PHP), Express
               \x1b[36mInfra\x1b[0m: Docker, Nginx, Linux, PM2, MySQL`
      break
    case 'about':
      outputText = `I am a software engineer with 10+ years of experience building real systems.
I prefer engineering robust systems that run in production over basic demos.
I deploy, manage, and maintain my own servers, and actively craft UI assets as a freelance designer.`
      break
    case 'skills':
      outputText = `\x1b[32m[Frontend]\x1b[0m: Vue.js, Nuxt.js, React, Tailwind CSS, JavaScript
\x1b[34m[Backend]\x1b[0m: Node.js, Express.js, Laravel, PHP, REST API
\x1b[35m[Database & Infra]\x1b[0m: MySQL, Docker, Nginx, Linux, Git, PM2
\x1b[33m[Other]\x1b[0m: AI Workflows, Automation Scripting, System Design, Multi-tenancy`
      break
    case 'projects':
      outputText = `1. \x1b[36mDistributor Inventory & Sales System\x1b[0m (Laravel + Filament + MySQL)
   - Multi warehouse, FIFO inventory, Stock ledger, SaaS architecture.
2. \x1b[36mUniversity Lab Information System\x1b[0m (Laravel + Vue + MySQL)
   - Lab scheduling, borrowing flow, inventory, and attendance tracking.
3. \x1b[36mDigital Invitation Platform\x1b[0m (PHP + JS + MySQL)
   - Running in production since 2022, handling real customer payments.
4. \x1b[36mAutomation & AI Tools\x1b[0m (Node.js + APIs)
   - Pipelines, custom script systems, and AI workflows.`
      break
    case 'clear':
      history.value = []
      inputCommand.value = ''
      return
    default:
      outputText = `Shell: command not found: ${commandText}. Type 'help' for options.`
  }

  history.value.push({ type: 'output', text: outputText })
  inputCommand.value = ''
  
  nextTick(() => {
    if (terminalBody.value) {
      terminalBody.value.scrollTop = terminalBody.value.scrollHeight
    }
  })
}

const formatText = (text) => {
  // Simple ANSI color simulator for terminal aesthetic
  return text
    .replace(/&/g, '&amp;')
    .replace(/</g, '&lt;')
    .replace(/>/g, '&gt;')
    .replace(/\x1b\[36m(.*?)\x1b\[0m/g, '<span class="text-brand-cyan font-semibold">$1</span>')
    .replace(/\x1b\[32m(.*?)\x1b\[0m/g, '<span class="text-brand-emerald font-semibold">$1</span>')
    .replace(/\x1b\[34m(.*?)\x1b\[0m/g, '<span class="text-brand-blue font-semibold">$1</span>')
    .replace(/\x1b\[35m(.*?)\x1b\[0m/g, '<span class="text-brand-purple font-semibold">$1</span>')
    .replace(/\x1b\[33m(.*?)\x1b\[0m/g, '<span class="text-amber-400 font-semibold">$1</span>')
}

const handleFormSubmit = () => {
  executeCommand(inputCommand.value)
}
</script>

<template>
  <div class="w-full max-w-2xl rounded-xl border border-white/10 bg-neutral-950/80 backdrop-blur-xl shadow-2xl overflow-hidden text-left flex flex-col font-mono text-xs">
    
    <!-- Title bar -->
    <div class="flex items-center justify-between px-4 py-3 bg-neutral-900/60 border-b border-white/5 select-none">
      <div class="flex items-center gap-1.5">
        <span class="w-3 h-3 rounded-full bg-rose-500/80"></span>
        <span class="w-3 h-3 rounded-full bg-amber-500/80"></span>
        <span class="w-3 h-3 rounded-full bg-emerald-500/80"></span>
      </div>
      <div class="flex items-center gap-1.5 text-[10px] text-neutral-500 font-medium">
        <TerminalIcon class="w-3.5 h-3.5 text-neutral-500" />
        <span>bash - feri@indie-builder:~</span>
      </div>
      <div class="w-12"></div>
    </div>

    <!-- Terminal Window -->
    <div
      ref="terminalBody"
      class="p-5 h-80 overflow-y-auto flex flex-col gap-3 font-mono leading-relaxed select-text"
    >
      <div v-for="(line, idx) in history" :key="idx" class="whitespace-pre-wrap">
        <!-- Input shell prompt -->
        <div v-if="line.type === 'input'" class="flex items-center gap-2">
          <span class="text-brand-cyan font-bold">feri-anggriawan ~$</span>
          <span class="text-neutral-200">{{ line.text }}</span>
        </div>
        
        <!-- Output text -->
        <div 
          v-else-if="line.type === 'output'" 
          v-html="formatText(line.text)"
          class="text-neutral-300 pl-2 border-l border-white/5 py-0.5"
        ></div>

        <!-- System text -->
        <div v-else class="text-neutral-500 italic">
          {{ line.text }}
        </div>
      </div>
    </div>

    <!-- Actions Panel (Shortcut Pills) -->
    <div class="px-5 py-3 border-t border-white/5 bg-neutral-900/25 flex flex-wrap items-center gap-2">
      <span class="text-[10px] text-neutral-500 uppercase tracking-widest mr-1">Shortcuts:</span>
      <button
        v-for="shortcut in shortcuts"
        :key="shortcut"
        @click="executeCommand(shortcut)"
        class="px-2.5 py-1 rounded bg-neutral-900 border border-white/10 hover:border-brand-cyan/40 hover:text-white text-[10px] text-neutral-400 transition-colors flex items-center gap-1 font-mono"
      >
        <Play class="w-2.5 h-2.5 text-brand-cyan" />
        <span>{{ shortcut }}</span>
      </button>
    </div>

    <!-- Input Form -->
    <form @submit.prevent="handleFormSubmit" class="flex items-center border-t border-white/5 bg-neutral-900/40 px-4 py-3">
      <span class="text-brand-cyan font-bold mr-2 select-none">feri-anggriawan ~$</span>
      <input
        v-model="inputCommand"
        type="text"
        placeholder="Type helper commands e.g. help, about..."
        class="bg-transparent border-none outline-none text-white flex-1 font-mono text-xs focus:ring-0 placeholder-neutral-600"
        autofocus
      />
      <button 
        type="submit"
        class="p-1 rounded text-neutral-400 hover:text-brand-cyan transition-colors"
      >
        <RefreshCw class="w-4 h-4" />
      </button>
    </form>
  </div>
</template>
