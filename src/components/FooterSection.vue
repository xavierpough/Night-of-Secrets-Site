<template>
  <footer class="footer-section" :style="footerBackgroundStyle">
    <div class="footer-section-inner container">
      <p class="footer-title">Connect with Night of Secrets</p>

      <nav class="footer-socials" aria-label="Social links">
        <a v-for="link in socials" :key="link.label" :href="link.href">{{ link.label }}</a>
      </nav>
    </div>
  </footer>
</template>

<script setup>
import footerBackground from '../img/NoS_Still_Jenna_Extended.png'

defineProps({
  socials: {
    type: Array,
    required: true,
  },
})

const footerBackgroundStyle = {
  backgroundImage: [
    'linear-gradient(180deg, rgba(8, 9, 17, 0.78), rgba(10, 8, 14, 0.92))',
    `url(${footerBackground})`,
  ].join(', '),
}
</script>

<style scoped src="../css/components/FooterSection.css"></style>
