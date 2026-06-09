<template>
  <div class="section-heading">
    <p class="section-eyebrow">{{ eyebrow }}</p>
    <slot name="title">
      <h2>{{ title }}</h2>
    </slot>
    <p v-if="subtitle" class="section-subtitle">{{ subtitle }}</p>
  </div>
</template>

<script setup>
defineProps({
  eyebrow: {
    type: String,
    default: '',
  },
  title: {
    type: String,
    required: true,
  },
  subtitle: {
    type: String,
    default: '',
  },
})
</script>

<style scoped src="../css/components/SectionTitle.css"></style>
