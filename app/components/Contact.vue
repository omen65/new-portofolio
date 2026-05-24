<script setup>
import { ref } from 'vue'
import { Mail, Send, CheckCircle2, ArrowRight } from '@lucide/vue'

const WA_NUMBER = '6282210182903'

const email = ref('')
const name = ref('')
const message = ref('')
const isSubmitting = ref(false)
const isSubmitted = ref(false)

const socialChannels = [
  { name: 'GitHub', value: '@omen65', href: 'https://github.com/omen65', color: 'text-white' },
  { name: 'LinkedIn', value: 'Feri Anggriawan', href: 'https://www.linkedin.com/in/feri-anggriawan-0309a414a/', color: 'text-brand-blue' },
  { name: 'WhatsApp', value: '+62 822-1018-2903', href: `https://wa.me/${WA_NUMBER}`, color: 'text-brand-emerald' },
  { name: 'Email', value: 'ferianggriawan.official.com', href: 'mailto:contact@ferianggriawan.com', icon: Mail, color: 'text-neutral-300' }
]

const handleFormSubmit = () => {
  if (!name.value || !email.value || !message.value) return

  isSubmitting.value = true

  const text = encodeURIComponent(
    `Hi Feri! I'm *${name.value}* (${email.value}).\n\n${message.value}`
  )

  setTimeout(() => {
    isSubmitting.value = false
    isSubmitted.value = true
    window.open(`https://wa.me/${WA_NUMBER}?text=${text}`, '_blank')
    name.value = ''
    email.value = ''
    message.value = ''
  }, 800)
}
</script>

<template>
  <section id="contact" class="py-24 relative overflow-hidden bg-neutral-950/40 border-t border-white/5">
    <div class="max-w-7xl mx-auto px-6 relative z-10">
      
      <!-- Section Header -->
      <div class="flex flex-col items-start gap-4 mb-16 max-w-xl text-left">
        <span class="text-xs font-mono font-semibold uppercase tracking-widest text-neutral-500 font-mono">Get in Touch</span>
        <h2 class="text-3xl sm:text-4xl font-bold tracking-tight text-white leading-tight">
          Let's Build Your Next System
        </h2>
        <div class="h-1 w-12 bg-gradient-to-r from-brand-cyan to-brand-emerald rounded-full"></div>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-12 gap-16 items-start">
        
        <!-- Left Side: Copywriting & Channels -->
        <div class="lg:col-span-5 flex flex-col gap-8 text-left">
          <div>
            <h3 class="text-xl font-bold text-white tracking-tight mb-3">
              Have a system or application to build?
            </h3>
            <p class="text-neutral-400 text-sm leading-relaxed">
              I build custom software tailored to real business workflows — from company profiles and POS systems to clinic applications, lab management, and full-scale ERP platforms. Every project is engineered to the same standard, regardless of scope.
            </p>
          </div>

          <!-- Social Details Grid -->
          <div class="flex flex-col gap-4 border-t border-white/5 pt-6">
            <a
              v-for="channel in socialChannels"
              :key="channel.name"
              :href="channel.href"
              target="_blank"
              rel="noopener noreferrer"
              class="flex items-center gap-4 p-4 rounded-xl border border-white/5 bg-neutral-900/20 hover:bg-neutral-900/50 hover:border-white/10 transition-all duration-300 group"
            >
              <div :class="['w-10 h-10 rounded-lg bg-neutral-950 border border-white/5 flex items-center justify-center transition-transform group-hover:scale-105', channel.color]">
                <!-- GitHub -->
                <svg v-if="channel.name === 'GitHub'" class="w-4 h-4" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M15 22v-4a4.8 4.8 0 0 0-1-3.5c3 0 6-2 6-5.5.08-1.25-.27-2.48-1-3.5.28-1.15.28-2.35 0-3.5 0 0-1 0-3 1.5-2.64-.5-5.36-.5-8 0C6 2 5 2 5 2c-.3 1.15-.3 2.35 0 3.5A5.403 5.403 0 0 0 4 9c0 3.5 3 5.5 6 5.5-.39.49-.68 1.05-.85 1.65-.17.6-.22 1.23-.15 1.85v4"></path><path d="M9 18c-4.51 2-5-2-7-2"></path></svg>
                <!-- LinkedIn -->
                <svg v-else-if="channel.name === 'LinkedIn'" class="w-4 h-4" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"></path><rect x="2" y="9" width="4" height="12"></rect><circle cx="4" cy="4" r="2"></circle></svg>
                <!-- WhatsApp -->
                <svg v-else-if="channel.name === 'WhatsApp'" class="w-4 h-4" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
                <!-- Email / fallback -->
                <component v-else :is="channel.icon" class="w-4 h-4" />
              </div>
              <div class="flex-1 min-w-0">
                <span class="block text-[10px] text-neutral-500 font-mono uppercase tracking-widest">{{ channel.name }}</span>
                <span class="block text-sm text-neutral-200 font-semibold truncate">{{ channel.value }}</span>
              </div>
              <ArrowRight class="w-4 h-4 text-neutral-600 transition-transform group-hover:translate-x-1" />
            </a>
          </div>
        </div>

        <!-- Right Side: Interactive Form -->
        <div class="lg:col-span-7 w-full">
          <div class="glass-panel rounded-xl p-8 transition-all relative border border-white/5 overflow-hidden">
            
            <!-- Success feedback state -->
            <div 
              v-if="isSubmitted" 
              class="absolute inset-0 bg-neutral-950/90 backdrop-blur flex flex-col items-center justify-center text-center p-8 z-30 transition-all"
            >
              <div class="w-16 h-16 rounded-full bg-brand-emerald/10 border border-brand-emerald/30 flex items-center justify-center text-brand-emerald mb-6 animate-bounce">
                <CheckCircle2 class="w-8 h-8" />
              </div>
              <h4 class="text-xl font-bold text-white tracking-tight mb-2">Message Sent Successfully</h4>
              <p class="text-neutral-400 text-xs max-w-xs leading-relaxed mb-6">
                Thank you for reaching out! I have received your email and will respond to your proposal within 24 hours.
              </p>
              <button 
                @click="isSubmitted = false"
                class="px-5 py-2.5 rounded-lg bg-white text-black font-semibold text-xs transition-all hover:bg-neutral-100 font-mono tracking-wider uppercase"
              >
                Send Another Message
              </button>
            </div>

            <!-- Standard Form structure -->
            <form @submit.prevent="handleFormSubmit" class="flex flex-col gap-6 text-left">
              <div class="grid grid-cols-1 sm:grid-cols-2 gap-6">
                <!-- Name -->
                <div class="flex flex-col gap-2">
                  <label for="name" class="text-[10px] text-neutral-500 font-mono uppercase tracking-widest">Full Name</label>
                  <input
                    id="name"
                    v-model="name"
                    type="text"
                    required
                    placeholder="E.g., John Doe"
                    class="w-full px-4 py-3 rounded-lg bg-neutral-950 border border-white/5 focus:border-brand-cyan/40 outline-none text-white text-xs transition-colors placeholder-neutral-700"
                  />
                </div>
                <!-- Email -->
                <div class="flex flex-col gap-2">
                  <label for="email" class="text-[10px] text-neutral-500 font-mono uppercase tracking-widest">Email Address</label>
                  <input
                    id="email"
                    v-model="email"
                    type="email"
                    required
                    placeholder="E.g., john@example.com"
                    class="w-full px-4 py-3 rounded-lg bg-neutral-950 border border-white/5 focus:border-brand-cyan/40 outline-none text-white text-xs transition-colors placeholder-neutral-700"
                  />
                </div>
              </div>

              <!-- Message -->
              <div class="flex flex-col gap-2">
                <label for="message" class="text-[10px] text-neutral-500 font-mono uppercase tracking-widest">Project Inquiry / Message</label>
                <textarea
                  id="message"
                  v-model="message"
                  required
                  rows="5"
                  placeholder="Describe your project system requirements, timeline, or business goals..."
                  class="w-full px-4 py-3 rounded-lg bg-neutral-950 border border-white/5 focus:border-brand-cyan/40 outline-none text-white text-xs transition-colors placeholder-neutral-700 resize-none"
                ></textarea>
              </div>

              <!-- Submit button -->
              <button
                type="submit"
                :disabled="isSubmitting"
                class="w-full py-3.5 rounded-lg bg-white hover:bg-neutral-100 disabled:bg-neutral-800 disabled:text-neutral-500 text-black font-semibold text-xs tracking-wider uppercase transition-all duration-300 hover:shadow-[0_0_20px_rgba(255,255,255,0.15)] flex items-center justify-center gap-2 group cursor-pointer"
              >
                <span v-if="!isSubmitting">Send via WhatsApp</span>
                <span v-else class="animate-pulse">Opening WhatsApp...</span>
                <svg class="w-3.5 h-3.5" viewBox="0 0 24 24" fill="currentColor"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/></svg>
              </button>
            </form>

          </div>
        </div>

      </div>

    </div>
  </section>
</template>
