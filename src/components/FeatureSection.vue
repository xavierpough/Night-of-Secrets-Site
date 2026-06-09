<template>
  <section :id="sectionId" :class="sectionClasses">
    <div :class="contentClasses">
    <div v-if="usePanel" class="panel mission-panel">
      <SectionTitle
        :eyebrow="eyebrow"
        :title="title"
        :subtitle="subtitle"
      />

      <p v-if="body" class="mission-copy">
        {{ body }}
      </p>

      <div :class="['feature-grid', columnsClass]">
        <article
          v-for="item in items"
          :key="item.title"
          :class="['panel', 'feature-card', { compact }]"
        >
          <div class="feature-icon">{{ item.icon }}</div>
          <h3>{{ item.title }}</h3>
          <p>{{ item.copy }}</p>
        </article>
      </div>
    </div>

    <template v-else>
      <SectionTitle
        :eyebrow="eyebrow"
        :title="title"
        :subtitle="subtitle"
      />

      <div :class="['feature-grid', columnsClass]">
        <article
          v-for="item in items"
          :key="item.title"
          class="panel feature-card"
        >
          <div class="feature-icon">{{ item.icon }}</div>
          <h3>{{ item.title }}</h3>
          <p>{{ item.copy }}</p>
        </article>
      </div>
    </template>
    </div>
  </section>
</template>

<script setup>
import { computed } from 'vue'
import SectionTitle from './SectionTitle.vue'

const props = defineProps({
  body: {
    type: String,
    default: '',
  },
  columns: {
    type: Number,
    default: 3,
  },
  compact: {
    type: Boolean,
    default: false,
  },
  eyebrow: {
    type: String,
    required: true,
  },
  fullBleed: {
    type: Boolean,
    default: false,
  },
  items: {
    type: Array,
    required: true,
  },
  sectionId: {
    type: String,
    default: '',
  },
  subtitle: {
    type: String,
    required: true,
  },
  title: {
    type: String,
    required: true,
  },
  usePanel: {
    type: Boolean,
    default: false,
  },
})

const columnsClass = computed(() => `feature-grid-${props.columns}`)
const sectionClasses = computed(() => [
  'section',
  'feature-section',
  { 'feature-section-full': props.fullBleed },
])
const contentClasses = computed(() => [
  { container: !props.fullBleed, 'feature-section-inner': props.fullBleed },
])
</script>

<style scoped src="../css/components/FeatureSection.css"></style>
