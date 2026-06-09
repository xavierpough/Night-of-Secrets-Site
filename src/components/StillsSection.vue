<template>
  <section class="section section-last stills-section">
    <div class="stills-section-inner">
      <SectionTitle
        eyebrow=""
        title="Stills"
        subtitle="Explore the suspenseful and chilling world of Night of Secrets through these stills from the series."
      />

      <div class="stills-carousel">
        <button
          class="stills-arrow stills-arrow-left"
          type="button"
          aria-label="Scroll stills left"
          @click="scrollByAmount(-1)"
        >
          <span></span>
        </button>

        <div ref="trackRef" class="stills-track">
          <article
            v-for="still in stills"
            :key="still.image"
            class="still-card"
          >
            <div class="still-card-frame">
              <img class="still-card-image" :src="still.image" :alt="still.title" />
            </div>
          </article>
        </div>

        <button
          class="stills-arrow stills-arrow-right"
          type="button"
          aria-label="Scroll stills right"
          @click="scrollByAmount(1)"
        >
          <span></span>
        </button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'
import SectionTitle from './SectionTitle.vue'

const trackRef = ref(null)

const stillModules = import.meta.glob('../img/Stills/*.{png,jpg,jpeg,webp,avif}', {
  eager: true,
  import: 'default',
  query: '?url',
})

const seenImages = new Set()
const stills = Object.entries(stillModules)
  .sort(([firstPath], [secondPath]) => firstPath.localeCompare(secondPath, undefined, { numeric: true }))
  .map(([path, image]) => ({
    title: path
      .split('/')
      .pop()
      .replace(/\.[^.]+$/, '')
      .replace(/[_-]/g, ' '),
    image,
  }))
  .filter((still) => {
    if (seenImages.has(still.image)) return false
    seenImages.add(still.image)
    return true
  })

const scrollByAmount = (direction) => {
  if (!trackRef.value) return

  const card = trackRef.value.querySelector('.still-card')
  const amount = card ? card.clientWidth * 0.9 : 320

  trackRef.value.scrollBy({
    left: amount * direction,
    behavior: 'smooth',
  })
}
</script>

<style scoped src="../css/components/StillsSection.css"></style>
