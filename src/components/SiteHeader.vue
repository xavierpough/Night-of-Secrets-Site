<template>
  <header class="topbar">
    <div class="topbar-inner container">
      <a class="brand brand-logo" href="#hero" aria-label="Night of Secrets home">
        <img class="brand-image" :src="filmLogo" alt="Night of Secrets logo" />
      </a>

      <button
        class="menu-toggle"
        type="button"
        :aria-expanded="isMenuOpen ? 'true' : 'false'"
        aria-controls="mobile-nav"
        aria-label="Toggle navigation menu"
        @click="toggleMenu"
      >
        <span></span>
        <span></span>
        <span></span>
      </button>

      <div :class="['nav-shell', { 'nav-shell-open': isMenuOpen }]">
        <nav id="mobile-nav" class="topnav" aria-label="Primary">
          <a
            v-for="item in navigation"
            :key="item.label"
            :href="item.href"
            @click="closeMenu"
          >
            {{ item.label }}
          </a>
        </nav>

        <a class="button button-primary button-small header-cta" href="#invest" @click="closeMenu">
          Invest Now
        </a>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref } from 'vue'
import filmLogo from '../img/NoS_Logo.png'

defineProps({
  navigation: {
    type: Array,
    required: true,
  },
})

const isMenuOpen = ref(false)

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const closeMenu = () => {
  isMenuOpen.value = false
}
</script>

<style scoped src="../css/components/SiteHeader.css"></style>
