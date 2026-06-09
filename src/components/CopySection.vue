<template>
  <section class="container section">
    <div class="panel mission-panel">
      <SectionTitle
        :eyebrow="eyebrow"
        :title="title"
        :subtitle="subtitle"
      />

      <p class="mission-copy">
        {{ body }}
      </p>
    </div>
  </section>
</template>

<script setup>
import SectionTitle from './SectionTitle.vue'

defineProps({
  body: {
    type: String,
    required: true,
  },
  eyebrow: {
    type: String,
    required: true,
  },
  subtitle: {
    type: String,
    required: true,
  },
  title: {
    type: String,
    required: true,
  },
})
</script>

<style scoped src="../css/components/CopySection.css"></style>
