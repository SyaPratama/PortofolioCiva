<template>
  <section id="about" class="about">
    <div class="container about__inner">
      <div class="about__image reveal">
        <div class="about__img-wrap">
          <img src="https://api.dicebear.com/9.x/lorelei/svg?seed=CivaCamelia2&backgroundColor=FFEBCC" alt="About Civa" />
          <div class="about__img-deco"></div>
        </div>
        <div class="about__exp-badge">
          <span class="exp-num">2+</span>
          <span class="exp-text">Tahun Berkarya</span>
        </div>
      </div>
      <div class="about__content">
        <p class="section-eyebrow reveal">Who I Am</p>
        <h2 class="section-title reveal">Passionate Creator,<br><em>Genuine Soul</em></h2>
        <p class="about__bio reveal">
          Halo! Aku <strong>Civa Camelia</strong>, seorang mahasiswi yang juga aktif sebagai
          content creator dan beauty vlogger. Aku percaya kecantikan itu bukan soal tampil sempurna,
          tapi soal percaya diri dan jadi diri sendiri.
        </p>
        <p class="about__bio reveal">
          Lewat konten-konten ku, aku berbagi review produk skincare & makeup, tips sehari-hari,
          hingga cerita kehidupan kampus yang relate banget buat kamu. Let's grow together! 🌸
        </p>
        <div class="about__details reveal">
          <div v-for="item in details" :key="item.label" class="detail-row">
            <span class="detail-label">{{ item.label }}</span>
            <span class="detail-value">
              <component :is="item.icon" v-if="item.icon" class="detail-icon" />
              {{ item.value }}
            </span>
          </div>
        </div>
        <a href="#contact" class="btn btn-primary reveal" style="margin-top:32px">Hubungi Aku</a>
      </div>
    </div>
  </section>
</template>

<script setup>
import { AcademicCapIcon, MapPinIcon } from '@heroicons/vue/24/outline'

const details = [
  { label: 'Nama',       value: 'Civa Camelia' },
  { label: 'Lokasi',     value: 'Indonesia', icon: MapPinIcon },
  { label: 'Status',     value: 'Siswi Aktif', icon: AcademicCapIcon },
  { label: 'Niche',      value: 'Beauty & Lifestyle' },
]
</script>

<style scoped>
.about { background: var(--peach); }
.about__inner { display: grid; grid-template-columns: 1fr 1.2fr; gap: 80px; align-items: center; }
.about__img-wrap {
  position: relative;
  width: 360px;
  height: 400px;
  border-radius: var(--radius-lg);
  overflow: hidden;
  box-shadow: var(--shadow-card);
}
.about__img-wrap img { width: 100%; height: 100%; object-fit: cover; }
.about__img-deco {
  position: absolute;
  inset: 0;
  background: linear-gradient(to bottom, transparent 60%, rgba(140,192,235,0.3));
}
.about__image { position: relative; }
.about__exp-badge {
  position: absolute;
  bottom: -20px; right: -20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  background: var(--blue);
  color: white;
  border-radius: var(--radius-md);
  padding: 16px 24px;
  box-shadow: var(--shadow-card);
  border: 4px solid var(--peach);
}
.exp-num { font-family: var(--font-display); font-size: 2rem; font-weight: 700; line-height: 1; }
.exp-text { font-size: 0.75rem; text-align: center; margin-top: 4px; opacity: 0.9; }
.section-eyebrow { font-size: 0.82rem; text-transform: uppercase; letter-spacing: 0.12em; font-weight: 600; color: var(--blue); margin-bottom: 12px; }
.section-title em { font-style: italic; color: var(--blue); }
.about__bio { color: var(--text-mid); line-height: 1.8; margin-top: 16px; }
.about__details { margin-top: 28px; display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
.detail-row { display: flex; flex-direction: column; gap: 2px; padding: 12px 16px; background: rgba(255,255,255,0.5); border-radius: var(--radius-sm); }
.detail-label { font-size: 0.75rem; text-transform: uppercase; letter-spacing: 0.08em; color: var(--text-light); }
.detail-value { font-size: 0.92rem; font-weight: 500; color: var(--text-dark); }
.detail-icon { width: 1rem; height: 1rem; margin-right: 0.25rem; }
@media (max-width: 900px) {
  .about__inner { grid-template-columns: 1fr; text-align: center; gap: 48px; }
  .about__image { display: flex; justify-content: center; }
  .about__img-wrap { width: 260px; height: 300px; }
  .about__details { grid-template-columns: 1fr 1fr; }
  .section-subtitle { margin: 12px auto 0; }
  .about__content .btn { margin: 32px auto 0; display: inline-flex; }
}
</style>
