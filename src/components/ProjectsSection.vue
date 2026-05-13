<template>
  <section id="projects" class="projects">
    <div class="container">
      <div class="projects__header">
        <p class="section-eyebrow reveal">Karya Saya</p>
        <h2 class="section-title reveal">Konten Terbaru</h2>
        <p class="section-subtitle reveal">Kumpulan video & konten favoritku yang sudah ditonton ribuan orang. Dari beauty review sampai cerita di sekolah!</p>
      </div>
      <div class="projects__grid">
        <article v-for="project in projects" :key="project.id" class="project-card reveal">
          <div class="project-visual" :style="{ background: project.bg }">
            <img :src="project.image" alt="project" class="project-image" />
          </div>
          <div class="project-info">
            <div class="project-tags">
              <span v-for="tag in project.tags" :key="tag" class="tag">{{ tag }}</span>
            </div>
            <h3 class="project-title">{{ project.title }}</h3>
            <p class="project-desc">{{ project.desc }}</p>
            <div class="project-links">
              <a :href="project.watch" class="btn btn-primary" target="_blank">Tonton Sekarang</a>
              <a :href="project.platform" class="btn btn-outline" target="_blank">{{ project.platformLabel }}</a>
            </div>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup>
const projects = [
  {
    id: 1, image: 'https://images.unsplash.com/photo-1596462502278-27bfdc403348?ixlib=rb-4.0.3&auto=format&fit=crop&w=300&q=80',
    bg: 'linear-gradient(135deg, #FFEBCC, #f9d4e8)',
    title: 'Full Glam Makeup Tutorial',
    desc: 'Tutorial makeup glam dari nol untuk pemula! Produk lokal semua, hasilnya tetap cetar dan tahan seharian.',
    tags: ['Beauty', 'Tutorial', 'Makeup'],
    watch: '#', platform: '#', platformLabel: 'YouTube',
  },
  {
    id: 2, image: 'https://images.unsplash.com/photo-1556228720-195a672e8a03?ixlib=rb-4.0.3&auto=format&fit=crop&w=300&q=80',
    bg: 'linear-gradient(135deg, #BFDDF0, #d4f5e9)',
    title: 'Skincare Routine Pagi & Malam',
    desc: 'Rutinitas skincare ku yang simpel tapi efektif. Cocok untuk kulit kombinasi dan budget pelajar!',
    tags: ['Skincare', 'Routine', 'Review'],
    watch: '#', platform: '#', platformLabel: 'YouTube',
  },
  {
    id: 3, image: 'https://images.unsplash.com/photo-1524504388940-b1c1722653e1?auto=format&fit=crop&w=300&q=80',
    bg: 'linear-gradient(135deg, #FFF9D2, #BFDDF0)',
    title: 'Day in My Life — Siswi Sibuk',
    desc: 'Ikutin keseharianku sebagai siswi yang sedang sekolah SMA, bikin konten, dan tetap waras. Relatable banget!',
    tags: ['Vlog', 'Lifestyle', 'Student Life'],
    watch: '#', platform: '#', platformLabel: 'Instagram',
  },
  {
    id: 4, image: 'https://images.unsplash.com/photo-1612817288484-6f916006741a?ixlib=rb-4.0.3&auto=format&fit=crop&w=300&q=80',
    bg: 'linear-gradient(135deg, #f0d4f5, #FFEBCC)',
    title: 'Review Produk Viral TikTok',
    desc: 'Aku cobain produk-produk yang lagi viral di TikTok — mana yang worth it, mana yang overhyped? Jujur banget!',
    tags: ['Review', 'Viral', 'Honest Review'],
    watch: '#', platform: '#', platformLabel: 'TikTok',
  },
]
</script>

<style scoped>
.projects { background: var(--sky); }
.projects__header { text-align: center; max-width: 560px; margin: 0 auto 56px; }
.section-eyebrow { font-size: 0.82rem; text-transform: uppercase; letter-spacing: 0.12em; font-weight: 600; color: var(--blue); margin-bottom: 12px; }
.section-subtitle { margin-top: 12px; color: var(--text-mid); }
.projects__grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); gap: 28px; }
.project-card { background: white; border-radius: var(--radius-lg); overflow: hidden; box-shadow: var(--shadow-soft); transition: var(--transition); }
.project-card:hover { transform: translateY(-6px); box-shadow: var(--shadow-card); }
.project-visual { height: 180px; display: flex; align-items: center; justify-content: center; }
.project-image { width: 100%; height: 100%; object-fit: cover; border-radius: var(--radius-md); }
.project-info { padding: 24px; }
.project-tags { display: flex; gap: 6px; flex-wrap: wrap; margin-bottom: 12px; }
.project-title { font-family: var(--font-display); font-size: 1.2rem; font-weight: 700; margin-bottom: 10px; color: var(--text-dark); }
.project-desc { font-size: 0.88rem; color: var(--text-mid); line-height: 1.7; margin-bottom: 20px; }
.project-links { display: flex; gap: 10px; }
.project-links .btn { padding: 9px 18px; font-size: 0.82rem; }
</style>
