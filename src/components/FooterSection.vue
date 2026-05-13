<template>
  <footer class="footer">
    <div class="container footer__inner">
      <div class="footer__brand">
        <a href="#hero" class="footer__logo">
          <span class="logo-dot"></span>
          Civa Camelia
        </a>
        <p class="footer__tagline">Content Creator · Beauty Vlogger · Student</p>
      </div>
      <div class="footer__links">
        <a v-for="item in navItems" :key="item.href" :href="item.href" class="footer-link">{{ item.label }}</a>
      </div>
      <p class="footer__copy">© Rasya Putra Pratama 2026. All rights reserved.</p>
    </div>
  </footer>
</template>

<script setup>
const navItems = [
  { href: '#about',    label: 'About' },
  { href: '#skills',   label: 'Skills' },
  { href: '#projects', label: 'Projects' },
  { href: '#contact',  label: 'Contact' },
]
</script>

<style scoped>
.footer { background: var(--blue); color: white; padding: 48px 0 32px; }
.footer__inner { display: flex; flex-direction: column; align-items: center; gap: 24px; text-align: center; }
.footer__logo { display: flex; align-items: center; gap: 8px; font-family: var(--font-display); font-size: 1.5rem; font-weight: 700; color: white; }
.logo-dot { width: 10px; height: 10px; border-radius: 50%; background: var(--cream); }
.footer__tagline { font-size: 0.88rem; opacity: 0.75; margin-top: 4px; }
.footer__links { display: flex; gap: 24px; flex-wrap: wrap; justify-content: center; }
.footer-link { font-size: 0.88rem; opacity: 0.8; transition: opacity 0.2s; }
.footer-link:hover { opacity: 1; }
.footer__copy { font-size: 0.8rem; opacity: 0.6; }
</style>
