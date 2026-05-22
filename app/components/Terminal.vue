<script setup>
import { ref, onMounted, nextTick } from 'vue'
import { Terminal as TerminalIcon, Play, RefreshCw } from '@lucide/vue'

const inputCommand = ref('')
const terminalBody = ref(null)

const history = ref([
  { type: 'system', text: 'Enterprise Engineering Node (Connected)' },
  { type: 'system', text: "Access level: Admin. Available commands: stack, specialization, experience, clear." },
  { type: 'input', text: 'stack' },
  { 
    type: 'output', 
    text: `\x1b[34m[Backend]\x1b[0m Laravel, Node.js, Express, PHP
\x1b[32m[Frontend]\x1b[0m Vue.js, Nuxt.js, React, Tailwind CSS
\x1b[36m[Mobile]\x1b[0m Internal Mobile Applications
\x1b[33m[Database]\x1b[0m MySQL, PostgreSQL
\x1b[35m[Infra]\x1b[0m Docker, Linux, Nginx, PM2` 
  }
])

const shortcuts = ['stack', 'specialization', 'experience', 'clear']

const executeCommand = (commandText) => {
  const cmd = commandText.trim().toLowerCase()
  if (!cmd) return

  history.value.push({ type: 'input', text: commandText })

  let outputText = ''
  switch (cmd) {
    case 'help':
      outputText = `Available commands:
  - \x1b[36mstack\x1b[0m          : View enterprise technology stack.
  - \x1b[36mspecialization\x1b[0m : View core engineering focuses.
  - \x1b[36mexperience\x1b[0m     : View professional summary.
  - \x1b[36mclear\x1b[0m          : Clear terminal history.`
      break
    case 'stack':
      outputText = `\x1b[34m[Backend]\x1b[0m Laravel, Node.js, Express, PHP
\x1b[32m[Frontend]\x1b[0m Vue.js, Nuxt.js, React, Tailwind CSS
\x1b[36m[Mobile]\x1b[0m Internal Mobile Applications
\x1b[33m[Database]\x1b[0m MySQL, PostgreSQL
\x1b[35m[Infra]\x1b[0m Docker, Linux, Nginx, PM2`
      break
    case 'specialization':
      outputText = `\x1b[36m> Custom ERP Systems\x1b[0m
  - Tailored enterprise resource planning for manufacturing and distribution.
\x1b[36m> Operational Platforms\x1b[0m
  - Lab management, logistics, POS, and digital business portals.
\x1b[36m> Internal Mobile Applications\x1b[0m
  - Seamless mobile integrations with legacy backend services.`
      break
    case 'experience':
      outputText = `\x1b[36m9+ Years Enterprise Software Engineering\x1b[0m
Building scalable software architecture based on real operational workflows.
Experienced in handling complex business requirements, long-term system maintenance,
and cross-departmental platform integrations.`
      break
    case 'clear':
      history.value = []
      inputCommand.value = ''
      return
    default:
      outputText = `Command not recognized: ${commandText}. Type 'help' for options.`
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
