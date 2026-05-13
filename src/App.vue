<template>
  <div id="app">
    <NavBar />
    <main>
      <HeroSection />
      <AboutSection />
      <SkillsSection />
      <ProjectsSection />
      <ContactSection />
    </main>
    <FooterSection />
    <!-- Scroll to top -->
    <button v-show="showTop" class="scroll-top" @click="scrollToTop" aria-label="Back to top">
      <ChevronUpIcon class="scroll-icon" />
    </button>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { ChevronUpIcon } from '@heroicons/vue/24/outline'
import NavBar from './components/NavBar.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import ProjectsSection from './components/ProjectsSection.vue'
import ContactSection from './components/ContactSection.vue'
import FooterSection from './components/FooterSection.vue'

const showTop = ref(false)

function scrollToTop() { window.scrollTo({ top: 0, behavior: 'smooth' }) }

function handleScroll() {
  showTop.value = window.scrollY > 500
  // Reveal on scroll
  document.querySelectorAll('.reveal:not(.visible)').forEach(el => {
    const rect = el.getBoundingClientRect()
    if (rect.top < window.innerHeight - 80) el.classList.add('visible')
  })
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
  handleScroll()
})
onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>

<style>
.scroll-top {
  position: fixed;
  bottom: 32px;
  right: 32px;
  width: 44px;
  height: 44px;
  border-radius: 50%;
  background: var(--blue);
  color: white;
  border: none;
  font-size: 1.1rem;
  cursor: pointer;
  box-shadow: var(--shadow-card);
  transition: var(--transition);
  z-index: 999;
  display: flex;
  align-items: center;
  justify-content: center;
}
  .scroll-top:hover { background: #6aacdf; transform: translateY(-3px); }
  .scroll-icon { width: 1.2rem; height: 1.2rem; }
  @media (max-width: 480px) { .scroll-top { bottom: 16px; right: 16px; } }
</style>
