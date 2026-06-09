<template>
  <section id="vision" class="section section-last vision-section" :style="visionBackgroundStyle">
    <div class="vision-section-inner container">
      <SectionTitle
        eyebrow=""
        title="See the Vision"
        subtitle="Experience the style and tone of Night of Secrets through teaser-driven story previews."
      />

      <div class="media-grid">
        <MediaCard
          v-for="media in mediaCards"
          :key="media.title"
          :item="media"
        />
      </div>
    </div>
  </section>
</template>

<script setup>
import { Fancybox } from '@fancyapps/ui'
import { onBeforeUnmount, onMounted } from 'vue'
import josieStill from '../img/NoS_Josie_Still.png'
import tylerStill from '../img/NoS_Still_Tyler_Still_2.png'
import MediaCard from './MediaCard.vue'
import SectionTitle from './SectionTitle.vue'

defineProps({
  mediaCards: {
    type: Array,
    required: true,
  },
})

const visionBackgroundStyle = {
  backgroundImage: [
    'linear-gradient(180deg, rgba(8, 10, 18, 0.1), rgba(12, 8, 16, 0.1))',
    `url(${josieStill})`,
    `url(${tylerStill})`,
  ].join(', '),
}

onMounted(() => {
  Fancybox.bind('[data-fancybox="vision-media"]', {
    animated: true,
    dragToClose: false,
  })
})

onBeforeUnmount(() => {
  Fancybox.unbind('[data-fancybox="vision-media"]')
})
</script>

<style scoped src="../css/components/VisionSection.css"></style>
