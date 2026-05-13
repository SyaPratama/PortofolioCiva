<template>
  <header :class="['navbar', { scrolled: isScrolled }]">
    <div class="container navbar__inner">
      <a href="#hero" class="navbar__logo">
        <span class="logo-dot"></span>
        Civa
      </a>
      <nav class="navbar__links">
        <a v-for="item in navItems" :key="item.href" :href="item.href" class="nav-link">{{ item.label }}</a>
      </nav>
      <a href="#contact" class="btn btn-primary navbar__cta">Hire Me</a>
      <button class="hamburger" @click="toggleMenu" :aria-expanded="menuOpen" aria-label="Toggle menu">
        <span></span><span></span><span></span>
      </button>
    </div>
    <div :class="['mobile-menu', { open: menuOpen }]">
      <a v-for="item in navItems" :key="item.href" :href="item.href" class="mobile-link" @click="menuOpen = false">{{ item.label }}</a>
      <a href="#contact" class="btn btn-primary" style="margin-top:8px" @click="menuOpen = false">Hire Me</a>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
const isScrolled = ref(false)
const menuOpen = ref(false)
const navItems = [
  { href: '#about', label: 'About' },
  { href: '#skills', label: 'Skills' },
  { href: '#projects', label: 'Projects' },
  { href: '#contact', label: 'Contact' },
]
function toggleMenu() { menuOpen.value = !menuOpen.value }
function handleScroll() { isScrolled.value = window.scrollY > 40 }
onMounted(() => window.addEventListener('scroll', handleScroll))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>

<style scoped>
.navbar { position: fixed; top: 0; left: 0; right: 0; z-index: 1000; padding: 20px 0; transition: all 0.4s ease; }
.navbar.scrolled { background: rgba(255,249,210,0.92); backdrop-filter: blur(12px); padding: 12px 0; box-shadow: 0 2px 24px rgba(140,192,235,0.2); }
.navbar__inner { display: flex; align-items: center; gap: 32px; }
.navbar__logo { display: flex; align-items: center; gap: 8px; font-family: var(--font-display); font-size: 1.4rem; font-weight: 700; color: var(--text-dark); }
.logo-dot { width: 10px; height: 10px; border-radius: 50%; background: var(--blue); }
.navbar__links { display: flex; gap: 4px; margin-left: auto; }
.nav-link { padding: 8px 16px; border-radius: var(--radius-full); font-size: 0.9rem; font-weight: 500; color: var(--text-mid); transition: var(--transition); }
.nav-link:hover { color: var(--text-dark); background: var(--sky); }
.navbar__cta { flex-shrink: 0; padding: 9px 22px; font-size: 0.88rem; }
.hamburger { display: none; flex-direction: column; gap: 5px; background: none; border: none; cursor: pointer; padding: 4px; margin-left: auto; }
.hamburger span { display: block; width: 24px; height: 2px; background: var(--text-dark); border-radius: 2px; }
.mobile-menu { display: none; flex-direction: column; align-items: center; gap: 4px; padding: 0 24px; background: rgba(255,249,210,0.97); backdrop-filter: blur(12px); max-height: 0; overflow: hidden; transition: max-height 0.4s ease, padding 0.4s ease; }
.mobile-menu.open { max-height: 400px; padding: 16px 24px 24px; }
.mobile-link { font-size: 1rem; font-weight: 500; color: var(--text-mid); padding: 10px 0; width: 100%; text-align: center; border-bottom: 1px solid var(--peach); }
@media (max-width: 768px) { .navbar__links, .navbar__cta { display: none; } .hamburger { display: flex; } .mobile-menu { display: flex; } }
</style>
