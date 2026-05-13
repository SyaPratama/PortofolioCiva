<template>
  <section id="skills" class="skills">
    <div class="container">
      <div class="skills__header">
        <p class="section-eyebrow reveal">What I Bring</p>
        <h2 class="section-title reveal">My Skills &<br>Expertise</h2>
        <p class="section-subtitle reveal">Kemampuan interpersonal dan komunikasi yang diasah melalui pengalaman nyata bersama banyak orang sebagai content creator dan siswi SMA.</p>
      </div>

      <div class="skills__categories reveal">
        <button
          v-for="cat in categories"
          :key="cat"
          :class="['cat-btn', { active: activeCategory === cat }]"
          @click="activeCategory = cat"
        >{{ cat }}</button>
      </div>

      <div class="skills__grid">
        <div
          v-for="skill in filteredSkills"
          :key="skill.name"
          class="skill-card reveal"
        >
          <component :is="skill.icon" class="skill-icon" />
          <h3 class="skill-name">{{ skill.name }}</h3>
          <div class="skill-bar-wrap">
            <div class="skill-bar">
              <div class="skill-fill" :style="{ width: skill.level + '%' }"></div>
            </div>
            <span class="skill-pct">{{ skill.level }}%</span>
          </div>
        </div>
      </div>

      <div class="tools-row reveal">
        <p class="tools-label">Pengalaman di:</p>
        <div class="tools-list">
          <span v-for="tool in tools" :key="tool" class="tag">{{ tool }}</span>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'
import { MicrophoneIcon, BookOpenIcon, SpeakerWaveIcon, UserGroupIcon, GlobeAltIcon, ChatBubbleLeftRightIcon, PencilIcon } from '@heroicons/vue/24/outline'

const activeCategory = ref('All')
const categories = ['All', 'Public Speaking', 'Sosialisasi', 'Komunikasi']

const skills = [
  { name: 'Presentasi Publik',    icon: MicrophoneIcon, level: 92, category: 'Public Speaking' },
  { name: 'Story Telling',        icon: BookOpenIcon, level: 88, category: 'Public Speaking' },
  { name: 'Moderator & MC',       icon: SpeakerWaveIcon, level: 85, category: 'Public Speaking' },
  { name: 'Networking',           icon: UserGroupIcon, level: 90, category: 'Sosialisasi' },
  { name: 'Teamwork',             icon: UserGroupIcon, level: 93, category: 'Sosialisasi' },
  { name: 'Adaptasi Lingkungan',  icon: GlobeAltIcon, level: 87, category: 'Sosialisasi' },
  { name: 'Komunikasi Verbal',    icon: ChatBubbleLeftRightIcon, level: 94, category: 'Komunikasi' },
  { name: 'Komunikasi Tertulis',  icon: PencilIcon, level: 89, category: 'Komunikasi' },
  { name: 'Active Listening',     icon: SpeakerWaveIcon, level: 91, category: 'Komunikasi' },
]

const tools = ['Seminar', 'Workshop', 'Diskusi Kelompok', 'Presentasi', 'Negosiasi', 'Mediasi']

const filteredSkills = computed(() =>
  activeCategory.value === 'All'
    ? skills
    : skills.filter(s => s.category === activeCategory.value)
)
</script>

<style scoped>
.skills { background: var(--cream); }
.skills__header { text-align: center; max-width: 560px; margin: 0 auto 48px; }
.section-eyebrow { font-size: 0.82rem; text-transform: uppercase; letter-spacing: 0.12em; font-weight: 600; color: var(--blue); margin-bottom: 12px; }
.section-subtitle { margin-top: 12px; color: var(--text-mid); }
.skills__categories { display: flex; justify-content: center; gap: 10px; flex-wrap: wrap; margin-bottom: 48px; }
.cat-btn { padding: 8px 22px; border-radius: var(--radius-full); border: 2px solid var(--sky); background: transparent; font-family: var(--font-body); font-size: 0.88rem; font-weight: 500; color: var(--text-mid); cursor: pointer; transition: var(--transition); }
.cat-btn.active, .cat-btn:hover { background: var(--blue); border-color: var(--blue); color: white; }
.skills__grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(240px, 1fr)); gap: 20px; margin-bottom: 48px; }
.skill-card { background: white; border-radius: var(--radius-md); padding: 24px; box-shadow: var(--shadow-soft); transition: var(--transition); border: 1px solid var(--peach); }
.skill-card:hover { transform: translateY(-4px); box-shadow: var(--shadow-card); }
.skill-icon { width: 1.8rem; height: 1.8rem; margin-bottom: 12px; }
.skill-name { font-size: 0.95rem; font-weight: 600; color: var(--text-dark); margin-bottom: 12px; }
.skill-bar-wrap { display: flex; align-items: center; gap: 10px; }
.skill-bar { flex: 1; height: 6px; background: var(--sky); border-radius: 3px; overflow: hidden; }
.skill-fill { height: 100%; background: linear-gradient(90deg, var(--blue), #6aacdf); border-radius: 3px; transition: width 1s ease; }
.skill-pct { font-size: 0.78rem; font-weight: 600; color: var(--blue); min-width: 36px; text-align: right; }
.tools-row { display: flex; align-items: center; gap: 16px; flex-wrap: wrap; padding: 24px; background: var(--peach); border-radius: var(--radius-md); }
.tools-label { font-size: 0.88rem; font-weight: 600; color: var(--text-mid); white-space: nowrap; }
.tools-list { display: flex; gap: 8px; flex-wrap: wrap; }
</style>
