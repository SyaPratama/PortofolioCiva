<template>
  <section id="hero" class="hero">
    <div class="hero__bg-blob blob-1"></div>
    <div class="hero__bg-blob blob-2"></div>
    <div class="container hero__inner">
      <div class="hero__content">
        <div class="hero__badge reveal">
          <span class="badge-dot"></span>
          Open for Collaboration ✨
        </div>
        <h1 class="hero__name reveal">
          Hi, I'm <span class="name-highlight">Civa<br>Camelia</span>
        </h1>
        <p class="hero__role reveal">Content Creator · Beauty Vlogger · <AcademicCapIcon class="role-icon" /> Siswi Aktif</p>
        <p class="hero__desc reveal">
          Berbagi cerita, tips kecantikan, dan perjalanan hidup sebagai siswi
          lewat konten yang autentik dan penuh warna. Based in Indonesia.
        </p>
        <div class="hero__actions reveal">
          <a href="#projects" class="btn btn-primary">Lihat Konten Saya</a>
          <a href="#contact" class="btn btn-outline">Kolaborasi Yuk!</a>
        </div>
        <div class="hero__stats reveal">
          <div v-for="stat in stats" :key="stat.label" class="stat-item">
            <span class="stat-num">{{ stat.value }}</span>
            <span class="stat-label">{{ stat.label }}</span>
          </div>
        </div>
      </div>
      <div class="hero__visual reveal">
        <div class="avatar-frame">
          <div class="avatar-inner">
            <img src="https://api.dicebear.com/9.x/lorelei/svg?seed=CivaCamelia&backgroundColor=BFDDF0" alt="Civa Camelia" class="avatar-img" />
          </div>
          <div class="avatar-badge">✦ Vlogger</div>
        </div>
        <div class="floating-card card-1">
          <PaintBrushIcon class="card-icon" />
          <span>Beauty</span>
        </div>
        <div class="floating-card card-2">
          <FilmIcon class="card-icon" />
          <span>Vlog</span>
        </div>
        <div class="floating-card card-3">
          <SparklesIcon class="card-icon" />
          <span>Lifestyle</span>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { onMounted } from 'vue'
import { PaintBrushIcon, FilmIcon, SparklesIcon, AcademicCapIcon } from '@heroicons/vue/24/outline'

const stats = [
  { value: '500+', label: 'Followers' },
  { value: '10+',  label: 'Video Dibuat' },
  { value: '2+',   label: 'Tahun Aktif' },
]
onMounted(() => {
  const els = document.querySelectorAll('.hero .reveal')
  els.forEach((el, i) => {
    setTimeout(() => el.classList.add('visible'), 150 + i * 120)
  })
})
</script>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  padding-top: 100px;
  position: relative;
  overflow: hidden;
  background: var(--cream);
}
.hero__bg-blob {
  position: absolute;
  border-radius: 50%;
  filter: blur(72px);
  opacity: 0.5;
  pointer-events: none;
}
.blob-1 { width: 500px; height: 500px; background: var(--sky); top: -100px; right: -100px; }
.blob-2 { width: 300px; height: 300px; background: var(--peach); bottom: 0; left: -80px; }
.hero__inner {
  display: grid;
  grid-template-columns: 1fr 1fr;
  align-items: center;
  gap: 64px;
  padding: 80px 0;
}
.hero__badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 6px 16px;
  background: var(--peach);
  border-radius: var(--radius-full);
  font-size: 0.85rem;
  font-weight: 500;
  margin-bottom: 24px;
  color: var(--text-dark);
}
.badge-dot { width: 8px; height: 8px; border-radius: 50%; background: #4caf50; animation: pulse 2s infinite; }
@keyframes pulse { 0%,100% { opacity: 1; } 50% { opacity: 0.4; } }
.hero__name {
  font-family: var(--font-display);
  font-size: clamp(2.8rem, 6vw, 5rem);
  font-weight: 900;
  line-height: 1.1;
  margin-bottom: 16px;
}
.name-highlight { color: var(--blue); }
.hero__role {
  font-size: 1.1rem;
  font-weight: 500;
  color: var(--text-mid);
  margin-bottom: 20px;
  letter-spacing: 0.02em;
}
.role-icon { width: 1.1rem; height: 1.1rem; display: inline; margin-right: 0.25rem; }
.hero__desc {
  font-size: 1rem;
  color: var(--text-mid);
  line-height: 1.8;
  max-width: 460px;
  margin-bottom: 36px;
}
.hero__actions { display: flex; gap: 16px; flex-wrap: wrap; margin-bottom: 48px; }
.hero__stats { display: flex; gap: 36px; }
.stat-item { display: flex; flex-direction: column; gap: 2px; }
.stat-num { font-family: var(--font-display); font-size: 1.8rem; font-weight: 700; color: var(--text-dark); }
.stat-label { font-size: 0.8rem; color: var(--text-light); text-transform: uppercase; letter-spacing: 0.06em; }
.hero__visual { position: relative; display: flex; justify-content: center; align-items: center; height: 480px; }
.avatar-frame {
  position: relative;
  width: 300px;
  height: 300px;
}
.avatar-inner {
  width: 100%;
  height: 100%;
  border-radius: 60% 40% 55% 45% / 50% 55% 45% 50%;
  background: linear-gradient(135deg, var(--sky), var(--blue));
  overflow: hidden;
  box-shadow: var(--shadow-card);
  animation: morph 8s ease-in-out infinite;
}
@keyframes morph {
  0%,100% { border-radius: 60% 40% 55% 45% / 50% 55% 45% 50%; }
  33%      { border-radius: 40% 60% 45% 55% / 55% 40% 60% 45%; }
  66%      { border-radius: 55% 45% 60% 40% / 45% 60% 40% 55%; }
}
.avatar-img { width: 100%; height: 100%; object-fit: cover; }
.avatar-badge {
  position: absolute;
  bottom: -12px; right: -12px;
  background: var(--peach);
  border: 3px solid var(--cream);
  border-radius: var(--radius-full);
  padding: 6px 18px;
  font-size: 0.85rem;
  font-weight: 600;
  color: var(--text-dark);
  box-shadow: var(--shadow-soft);
}
.floating-card {
  position: absolute;
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 10px 18px;
  background: white;
  border-radius: var(--radius-md);
  box-shadow: var(--shadow-card);
  font-size: 0.85rem;
  font-weight: 500;
  animation: float 4s ease-in-out infinite;
}
.card-1 { top: 20px; left: -20px; animation-delay: 0s; }
.card-2 { bottom: 60px; right: -20px; animation-delay: 1.5s; }
.card-3 { top: 60%; left: -30px; animation-delay: 0.8s; }
.card-icon { width: 1.1rem; height: 1.1rem; }
@keyframes float {
  0%,100% { transform: translateY(0); }
  50%      { transform: translateY(-10px); }
}
@media (max-width: 900px) {
  .hero__inner { grid-template-columns: 1fr; text-align: center; gap: 48px; }
  .hero__desc { margin: 0 auto 36px; }
  .hero__actions { justify-content: center; }
  .hero__stats { justify-content: center; }
  .hero__visual { height: 320px; }
  .avatar-frame { width: 220px; height: 220px; }
  .card-1 { left: 0; top: 0; }
  .card-2 { right: 0; }
  .card-3 { left: -10px; }
}
@media (max-width: 480px) {
  .hero__visual { display: none; }
}
</style>
