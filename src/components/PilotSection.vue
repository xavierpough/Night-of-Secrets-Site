<template>
  <section id="pilot" class="section pilot-section">
    <div class="pilot-section-inner">
      <header class="pilot-header">
        <img class="pilot-title-art" :src="shadowsTitle" :alt="pilot.titleAlt" />
        <h2>{{ pilot.eyebrow }}</h2>
        <p>{{ pilot.tagline }}</p>
      </header>

      <div class="pilot-grid">
        <div class="pilot-copy">
          <h3>{{ pilot.heading }}</h3>
          <p v-for="paragraph in pilot.paragraphs" :key="paragraph">
            {{ paragraph }}
          </p>

          <div class="panel recognition-card">
            <h3>Recognized by Industry Experts</h3>
            <p>{{ pilot.recognition }}</p>

            <div class="award-grid">
              <div class="award-card">
                <img :src="filmmaticAward" alt="Filmmatic Horror Screenplay Awards quarter-finalist" />
              </div>
              <div class="award-card">
                <img :src="laAward" alt="Los Angeles International Screenplay Awards quarter finalist" />
              </div>
            </div>
          </div>
        </div>

        <aside class="pilot-cover panel">
          <img :src="shadowsCover" alt="Shadows pilot cover art" />
        </aside>
      </div>

      <div class="pilot-pillars">
        <article
          v-for="pillar in pilot.pillars"
          :key="pillar.title"
          class="pilot-pillar"
        >
          <span>{{ pillar.icon }}</span>
          <h4>{{ pillar.title }}</h4>
          <p>{{ pillar.copy }}</p>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup>
import filmmaticAward from '../img/Shadows/Filmmatic_Horror_Screenplay_Awards.png'
import laAward from '../img/Shadows/Los_Angeles_Screenplay_Awards.png'
import shadowsCover from '../img/Shadows/Shadows_Cover_Art.png'
import shadowsTitle from '../img/Shadows/Shadows_Text.png'

defineProps({
  pilot: {
    type: Object,
    required: true,
  },
})
</script>

<style scoped src="../css/components/PilotSection.css"></style>
