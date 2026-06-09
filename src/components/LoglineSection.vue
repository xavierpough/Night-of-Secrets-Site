<template>
  <section
    id="logline"
    ref="loglineSection"
    class="logline-section"
    aria-labelledby="logline-title"
  >
    <div class="logline-video" aria-hidden="true">
      <iframe
        class="logline-video-frame"
        :src="vimeoBackgroundUrl"
        title="Night of Secrets mood footage"
        allow="autoplay; fullscreen; picture-in-picture"
        referrerpolicy="strict-origin-when-cross-origin"
      ></iframe>
    </div>

    <div class="logline-overlay"></div>

    <div class="container logline-content">
      <p class="logline-copy" :aria-label="logline">
        <span class="logline-copy-measure" aria-hidden="true">{{ logline }}</span>
        <span class="logline-typewriter" aria-hidden="true">
          {{ displayedLogline }}<span v-if="isTyping" class="logline-caret"></span>
        </span>
      </p>
    </div>
  </section>
</template>

<script setup>
import { onBeforeUnmount, onMounted, ref, watch } from 'vue'

const props = defineProps({
  logline: {
    type: String,
    required: true,
  },
})

const vimeoBackgroundUrl =
  'https://player.vimeo.com/video/1197429579?background=1&autoplay=1&loop=1&muted=1&controls=0&autopause=0&playsinline=1'

const loglineSection = ref(null)
const displayedLogline = ref('')
const isTyping = ref(false)
const hasStartedTyping = ref(false)
let typingTimer = null
let sectionObserver = null

const clearTypingTimer = () => {
  if (typingTimer) {
    window.clearTimeout(typingTimer)
    typingTimer = null
  }
}

const shouldReduceMotion = () =>
  window.matchMedia?.('(prefers-reduced-motion: reduce)').matches

const typeLogline = () => {
  clearTypingTimer()
  hasStartedTyping.value = true

  if (shouldReduceMotion()) {
    displayedLogline.value = props.logline
    isTyping.value = false
    return
  }

  displayedLogline.value = ''
  isTyping.value = true

  const revealNextCharacter = () => {
    const nextLength = displayedLogline.value.length + 1
    displayedLogline.value = props.logline.slice(0, nextLength)

    if (nextLength < props.logline.length) {
      typingTimer = window.setTimeout(revealNextCharacter, 43)
      return
    }

    isTyping.value = false
    typingTimer = null
  }

  typingTimer = window.setTimeout(revealNextCharacter, 432)
}

onMounted(() => {
  if (!('IntersectionObserver' in window) || shouldReduceMotion()) {
    typeLogline()
    return
  }

  sectionObserver = new IntersectionObserver(
    ([entry]) => {
      if (!entry.isIntersecting) {
        return
      }

      typeLogline()
      sectionObserver?.disconnect()
      sectionObserver = null
    },
    { threshold: 0.35 },
  )

  if (loglineSection.value) {
    sectionObserver.observe(loglineSection.value)
  }
})

onBeforeUnmount(() => {
  clearTypingTimer()
  sectionObserver?.disconnect()
})

watch(() => props.logline, () => {
  if (hasStartedTyping.value) {
    typeLogline()
  }
})
</script>

<style scoped src="../css/components/LoglineSection.css"></style>
