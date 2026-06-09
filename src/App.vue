<template>
  <div class="site-shell">
    <div class="site-backdrop"></div>

    <SiteHeader :navigation="navigation" />

    <main>
      <HeroSection />
      <LoglineSection :logline="logline" />
      <VisionSection :media-cards="mediaCards" />
      <StillsSection />
      <AboutSection :story="story" />
      <PilotSection :pilot="pilotScript" />
      <FundingSection :funding="funding" />
      <FeatureSection
        section-id="invest"
        eyebrow="Why Invest"
        title="Why Investors Fund Night of Secrets"
        subtitle="A clear blend of concept strength, visual identity, and audience-facing upside."
        :items="investorFeatures"
        :full-bleed="true"
      />
      <FeatureSection
        eyebrow="Why It Needs To Be Made"
        title="Night of Secrets Needs To Be Made"
        subtitle="A high-concept visual mystery that invites repeat engagement while opening the door to long-term franchise growth."
        :body="missionCopy"
        :items="missionReasons"
        :columns="4"
        :compact="true"
        :use-panel="true"
      />
      <CopySection
        eyebrow="Funding Goal"
        title="Why We Need Funding"
        subtitle="Funding helps us reach the quality bar required for independent production, post-production, marketing, and festival positioning."
        :body="fundingNeedCopy"
      />
      <RoadmapSection :roadmap="roadmap" />
      <FooterSection :socials="socials" />
    </main>
  </div>
</template>

<script setup>
import AboutSection from './components/AboutSection.vue'
import CopySection from './components/CopySection.vue'
import FooterSection from './components/FooterSection.vue'
import FeatureSection from './components/FeatureSection.vue'
import FundingSection from './components/FundingSection.vue'
import HeroSection from './components/HeroSection.vue'
import LoglineSection from './components/LoglineSection.vue'
import PilotSection from './components/PilotSection.vue'
import RoadmapSection from './components/RoadmapSection.vue'
import SiteHeader from './components/SiteHeader.vue'
import StillsSection from './components/StillsSection.vue'
import VisionSection from './components/VisionSection.vue'
import {
  funding,
  fundingNeedCopy,
  investorFeatures,
  logline,
  mediaCards,
  missionCopy,
  missionReasons,
  navigation,
  pilotScript,
  roadmap,
  socials,
  story,
} from './data/siteContent'
</script>

<style scoped src="./css/App.css"></style>
