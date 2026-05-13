<template>
  <section id="contact" class="contact">
    <div class="container contact__inner">
      <div class="contact__info">
        <p class="section-eyebrow reveal">Say Hello</p>
        <h2 class="section-title reveal">Yuk,<br><em>Kolaborasi!</em></h2>
        <p class="contact__desc reveal">
          Mau collab bareng, endorse produk, atau sekadar say hi? Aku terbuka untuk
          semua bentuk kerja sama yang fun dan meaningful. Reach out ya! 💌
        </p>
        <div class="contact__cards reveal">
          <div v-for="item in contactItems" :key="item.label" class="contact-card">
            <component :is="item.icon" class="contact-icon" />
            <div>
              <p class="contact-card-label">{{ item.label }}</p>
              <a :href="item.href" class="contact-card-value">{{ item.value }}</a>
            </div>
          </div>
        </div>
        <div class="social-links reveal">
          <a v-for="s in socials" :key="s.name" :href="s.href" class="social-btn" target="_blank" :aria-label="s.name">
            <div v-html="s.svg" class="social-svg"></div>
          </a>
        </div>
      </div>

      <form class="contact__form reveal" @submit.prevent="handleSubmit">
        <div class="form-group">
          <label>Your Name</label>
          <input v-model="form.name" type="text" placeholder="Nama kamu" required />
        </div>
        <div class="form-group">
          <label>Email</label>
          <input v-model="form.email" type="email" placeholder="email@contoh.com" required />
        </div>
        <div class="form-group">
          <label>Jenis Kolaborasi</label>
          <input v-model="form.subject" type="text" placeholder="Endorse / Collab Video / dll" />
        </div>
        <div class="form-group">
          <label>Pesan</label>
          <textarea v-model="form.message" rows="5" placeholder="Ceritain ideamu di sini..." required></textarea>
        </div>
        <button type="submit" class="btn btn-primary submit-btn" :disabled="submitted">
          <span v-if="!submitted">Kirim Pesan 💌</span>
          <span v-else">Terkirim! 🎉</span>
        </button>
      </form>
    </div>
  </section>
</template>

<script setup>
import { ref, reactive } from 'vue'
import { EnvelopeIcon, MapPinIcon, SparklesIcon } from '@heroicons/vue/24/outline'

const submitted = ref(false)
const form = reactive({ name: '', email: '', subject: '', message: '' })
function handleSubmit() {
  submitted.value = true
  setTimeout(() => { submitted.value = false; Object.assign(form, { name:'', email:'', subject:'', message:'' }) }, 3000)
}
const contactItems = [
  { icon: EnvelopeIcon, label: 'Email',        value: 'civa@gmail.com',    href: 'mailto:civa@gmail.com' },
  { icon: MapPinIcon, label: 'Lokasi',       value: 'Indonesia 🇮🇩',        href: '#' },
  { icon: SparklesIcon, label: 'Open untuk',   value: 'Endorsement & Collab', href: '#' },
]
const socials = [
  { name: 'YouTube',    svg: '<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polygon points="23 7 16 12 23 17 23 7"></polygon><rect x="1" y="5" width="15" height="14" rx="2" ry="2"></rect></svg>',  href: 'https://youtube.com/' },
  { name: 'Instagram',  svg: '<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="2" width="20" height="20" rx="5" ry="5"></rect><path d="m16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"></path><line x1="17.5" y1="6.5" x2="17.51" y2="6.5"></line></svg>',  href: 'https://instagram.com/' },
  { name: 'TikTok',     svg: '<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M9 12a4 4 0 1 0 4 4V4a5 5 0 0 1 5 5"></path></svg>',  href: 'https://tiktok.com/' },
  { name: 'Twitter/X',  svg: '<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M23 3a10.9 10.9 0 0 1-3.14 1.53 4.48 4.48 0 0 0-7.86 3v1A10.66 10.66 0 0 1 3 4s-4 9 5 13a11.64 11.64 0 0 1-7 2c9 5 20 0 20-11.5a4.5 4.5 0 0 0-.08-.83A7.72 7.72 0 0 0 23 3z"></path></svg>',  href: 'https://twitter.com/' },
]
</script>

<style scoped>
.contact { background: var(--cream); }
.contact__inner { display: grid; grid-template-columns: 1fr 1.3fr; gap: 80px; align-items: start; }
.section-eyebrow { font-size: 0.82rem; text-transform: uppercase; letter-spacing: 0.12em; font-weight: 600; color: var(--blue); margin-bottom: 12px; }
.section-title em { font-style: italic; color: var(--blue); }
.contact__desc { color: var(--text-mid); line-height: 1.8; margin-top: 16px; margin-bottom: 32px; }
.contact__cards { display: flex; flex-direction: column; gap: 16px; margin-bottom: 32px; }
.contact-card { display: flex; align-items: center; gap: 16px; padding: 16px; background: var(--peach); border-radius: var(--radius-md); }
.contact-icon { width: 1.4rem; height: 1.4rem; flex-shrink: 0; }
.contact-card-label { font-size: 0.75rem; text-transform: uppercase; letter-spacing: 0.08em; color: var(--text-light); }
.contact-card-value { font-size: 0.95rem; font-weight: 500; color: var(--text-dark); }
.contact-card-value:hover { color: var(--blue); }
.social-links { display: flex; gap: 10px; }
.social-btn { width: 44px; height: 44px; display: flex; align-items: center; justify-content: center; background: var(--sky); border-radius: var(--radius-sm); font-size: 1.2rem; transition: var(--transition); text-decoration: none; }
.social-svg { width: 20px; height: 20px; }
.social-btn:hover { background: var(--blue); transform: translateY(-2px); }
.contact__form { background: white; border-radius: var(--radius-lg); padding: 40px; box-shadow: var(--shadow-card); border: 1px solid var(--peach); }
.form-group { display: flex; flex-direction: column; gap: 6px; margin-bottom: 20px; }
.form-group label { font-size: 0.82rem; font-weight: 600; color: var(--text-mid); text-transform: uppercase; letter-spacing: 0.06em; }
.form-group input,
.form-group textarea {
  padding: 12px 16px;
  border: 2px solid var(--sky);
  border-radius: var(--radius-sm);
  font-family: var(--font-body);
  font-size: 0.92rem;
  color: var(--text-dark);
  background: var(--cream);
  transition: var(--transition);
  outline: none;
  resize: vertical;
}
.form-group input:focus,
.form-group textarea:focus { border-color: var(--blue); background: white; }
.form-group input::placeholder,
.form-group textarea::placeholder { color: var(--text-light); }
.submit-btn { width: 100%; justify-content: center; padding: 14px; font-size: 1rem; }
.submit-btn:disabled { opacity: 0.7; cursor: default; transform: none; }
@media (max-width: 900px) {
  .contact__inner { grid-template-columns: 1fr; gap: 48px; }
}
</style>
