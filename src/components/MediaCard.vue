<template>
  <article class="media-card panel">
    <a
      v-if="item.videoUrl"
      class="media-thumb"
      :class="[item.variant, { 'has-image': item.thumbnail }]"
      :href="item.videoUrl"
      :style="thumbnailStyle"
      data-fancybox="vision-media"
      data-type="iframe"
      :data-caption="item.title"
      :aria-label="`Play ${item.title}`"
    >
      <span class="play-button" aria-hidden="true"></span>
    </a>
    <div
      v-else
      class="media-thumb"
      :class="[item.variant, { 'has-image': item.thumbnail }]"
      :style="thumbnailStyle"
    >
      <span class="play-button" aria-hidden="true"></span>
    </div>
    <h3>{{ item.title }}</h3>
    <p>{{ item.copy }}</p>
  </article>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  item: {
    type: Object,
    required: true,
  },
})

const thumbnailStyle = computed(() => {
  if (!props.item.thumbnail) {
    return {}
  }

  return {
    '--media-thumbnail': `url(${props.item.thumbnail})`,
  }
})
</script>

<style scoped src="../css/components/MediaCard.css"></style>
