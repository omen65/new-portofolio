<script setup>
import { ref } from 'vue'

const cardRef = ref(null)
const mouseX = ref(0)
const mouseY = ref(0)
const isHovered = ref(false)

const handleMouseMove = (e) => {
  if (!cardRef.value) return
  const rect = cardRef.value.getBoundingClientRect()
  mouseX.value = e.clientX - rect.left
  mouseY.value = e.clientY - rect.top
}

const handleMouseEnter = () => {
  isHovered.value = true
}

const handleMouseLeave = () => {
  isHovered.value = false
}
</script>

<template>
  <div
    ref="cardRef"
    @mousemove="handleMouseMove"
    @mouseenter="handleMouseEnter"
    @mouseleave="handleMouseLeave"
    class="relative rounded-xl border border-white/5 bg-neutral-900/40 backdrop-blur-md overflow-hidden transition-all duration-300 p-6 flex flex-col justify-between h-full group"
  >
    <!-- Background Radial Glow -->
    <div
      class="pointer-events-none absolute inset-0 transition-opacity duration-300 opacity-0 group-hover:opacity-100"
      :style="{
        background: `radial-gradient(350px circle at ${mouseX}px ${mouseY}px, rgba(59, 130, 246, 0.1), transparent)`
      }"
    ></div>

    <!-- Fine Border Spotlight Glow -->
    <div
      class="pointer-events-none absolute inset-0 transition-opacity duration-300 opacity-0 group-hover:opacity-100"
      :style="{
        background: `radial-gradient(200px circle at ${mouseX}px ${mouseY}px, rgba(255, 255, 255, 0.08), transparent)`
      }"
    ></div>

    <div class="relative z-10 flex flex-col justify-between h-full w-full">
      <slot></slot>
    </div>
  </div>
</template>
