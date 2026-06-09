<template>
  <section id="about" class="section about-section" :style="sectionBackgroundStyle">
    <div class="about-section-inner">
      <header class="about-header">
        <p class="about-eyebrow">{{ story.eyebrow }}</p>
        <h2 class="about-title">
          <span>What Is</span>
          <img :src="titleImage" alt="Night of Secrets" />
        </h2>
        <p>{{ story.subtitle }}</p>
      </header>

      <div class="about-grid">
        <div class="story-poster panel">
          <img class="poster-image" :src="filmCover" alt="Night of Secrets film poster" />
        </div>

        <div class="panel story-copy about-panel">
          <p class="story-intro">{{ story.intro }}</p>

          <div class="about-panel-grid">
            <div class="purpose-column">
              <h3>Our Purpose</h3>
              <p>{{ story.purpose }}</p>
              <p class="purpose-lead">Night of Secrets is designed to:</p>

              <div class="purpose-list">
                <article
                  v-for="item in story.purposeItems"
                  :key="item.title"
                  class="purpose-item"
                >
                  <span>{{ item.icon }}</span>
                  <div>
                    <strong>{{ item.title }}</strong>
                    <p>{{ item.copy }}</p>
                  </div>
                </article>
              </div>
            </div>

            <aside class="universe-column">
              <h3>{{ story.universe.title }}</h3>
              <div class="universe-card">
                <img :src="shadowsTitle" alt="Shadows" />
                <strong>{{ story.universe.mainSubtitle }}</strong>
                <p>{{ story.universe.mainCopy }}</p>
              </div>

              <div class="universe-arrow" aria-hidden="true"></div>

              <div class="universe-card universe-card-nos">
                <img :src="titleImage" :alt="story.universe.prequelTitle" />
                <span>{{ story.universe.prequelSubtitle }}</span>
                <p>{{ story.universe.prequelCopy }}</p>
              </div>

              <div class="universe-future">
                <strong>{{ story.universe.futureTitle }}</strong>
                <p>{{ story.universe.futureCopy }}</p>
              </div>
            </aside>
          </div>
        </div>
      </div>

      <div class="badge-grid">
        <article
          v-for="badge in story.badges"
          :key="badge.title"
          class="info-badge panel"
        >
          <span class="badge-icon">{{ badge.icon }}</span>
          <div>
            <strong>{{ badge.title }}</strong>
            <p>{{ badge.copy }}</p>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup>
import filmCover from '../img/NoS_Film_Cover.png'
import sectionBackground from '../img/NoS_Still_Jenna_Extended.png'
import titleImage from '../img/NoS_Title.png'
import shadowsTitle from '../img/Shadows/Shadows_Text.png'

defineProps({
  story: {
    type: Object,
    required: true,
  },
})

const sectionBackgroundStyle = {
  backgroundImage: [
    'linear-gradient(180deg, rgba(8, 10, 18, 0.44), rgba(14, 9, 18, 0.38))',
    `url(${sectionBackground})`,
  ].join(', '),
}
</script>

<style scoped src="../css/components/AboutSection.css"></style>
