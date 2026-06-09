<template>
  <section id="progress" class="container section">
    <div class="panel funding-panel">
      <SectionTitle
        eyebrow="Funding Progress"
        title="Help Bring Night of Secrets to Life"
        subtitle="Every contribution moves the series closer to production, festivals, and audience growth."
      />

      <div class="funding-summary">
        <div>
          <p class="funding-raised">${{ funding.raised.toLocaleString() }} Raised So Far</p>
          <p class="funding-goal">Goal: ${{ funding.goal.toLocaleString() }}</p>
        </div>

        <div class="funding-stats">
          <strong>{{ funding.percent }}%</strong>
          <span>Campaign Active</span>
        </div>
      </div>

      <div class="progress" aria-label="Funding progress">
        <div class="progress-track">
          <div class="progress-fill" :style="{ width: `${funding.percent}%` }"></div>
        </div>
        <div class="progress-scale">
          <span v-for="marker in funding.markers" :key="marker">{{ marker }}</span>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import SectionTitle from './SectionTitle.vue'

defineProps({
  funding: {
    type: Object,
    required: true,
  },
})
</script>

<style scoped src="../css/components/FundingSection.css"></style>
