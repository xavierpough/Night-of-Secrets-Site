<template>
  <section id="hero" class="hero">
    <div class="hero-inner">
      <div class="hero-visual" :style="heroBackgroundStyle" aria-hidden="true"></div>

      <div class="hero-copy">
        <p class="hero-kicker">Some secrets were meant to stay buried.</p>
        <img class="title-image" :src="titleImage" alt="Night of Secrets" />
        <p class="hero-subtitle">
          A dark, cinematic slasher mystery series built to blend prestige horror,
          fan intrigue, and franchise-level potential.
        </p>

        <div class="hero-actions">
          <a class="button button-primary" href="#invest">Invest in the Project</a>
          <a class="button button-secondary" href="#vision">Watch Teaser</a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import coverImage from '../img/NoS_Cover_Extended.png'
import titleImage from '../img/NoS_Title.png'

const heroBackgroundStyle = {
  backgroundImage: [
    `url(${coverImage})`,
  ].join(', '),
}
</script>

<style scoped src="../css/components/HeroSection.css"></style>
