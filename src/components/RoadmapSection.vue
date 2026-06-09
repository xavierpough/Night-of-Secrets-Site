<template>
  <section id="roadmap" class="container section">
    <div class="panel mission-panel">
      <SectionTitle
        eyebrow="Project Roadmap"
        title="Project Roadmap"
        subtitle="Experience the style and tone of Night of Secrets from development through audience expansion."
      />

      <div class="roadmap">
        <div class="roadmap-line"></div>
        <article
          v-for="step in roadmap"
          :key="step.title"
          class="roadmap-step"
        >
          <div class="roadmap-node"></div>
          <h3>{{ step.title }}</h3>
          <p>{{ step.copy }}</p>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup>
import SectionTitle from './SectionTitle.vue'

defineProps({
  roadmap: {
    type: Array,
    required: true,
  },
})
</script>

<style scoped src="../css/components/RoadmapSection.css"></style>
