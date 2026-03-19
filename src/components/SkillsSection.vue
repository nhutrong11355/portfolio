<template>
  <section id="skills" class="skills">
    <div class="container">
      <h2 class="section-title reveal-up" ref="titleRef" :class="{ visible: titleVisible }">Skills & Technologies</h2>
      <div class="skills-grid stagger-children" ref="gridRef" :class="{ visible: gridVisible }">
        <div v-for="category in categories" :key="category.title" class="skill-category">
          <h3>{{ category.title }}</h3>
          <div class="skill-items">
            <div v-for="skill in category.skills" :key="skill.name" class="skill-item">
              <div class="skill-header">
                <span v-if="skill.img" class="skill-icon"><img :src="skill.img" :alt="skill.name" /></span>
                <span v-else class="skill-icon">{{ skill.icon }}</span>
                <span class="skill-name">{{ skill.name }}</span>
                <span class="skill-level">{{ skill.level }}%</span>
              </div>
              <div class="skill-bar">
                <div class="skill-bar-fill" :style="{ width: gridVisible ? skill.level + '%' : '0%' }"></div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { useScrollReveal } from '../composables/useScrollReveal'
import laravelIcon from '../assets/laravel.svg'
const { elementRef: titleRef, isVisible: titleVisible } = useScrollReveal()
const { elementRef: gridRef, isVisible: gridVisible } = useScrollReveal({ threshold: 0.1 })

const categories = [
  {
    title: '🔧 Backend & Frameworks',
    skills: [
      { name: 'PHP', icon: '🐘', level: 90 },
      { name: 'Laravel', img: laravelIcon, level: 90 },
      { name: 'MySQL', icon: '🗄️', level: 85 },
      { name: 'API Design', icon: '🔌', level: 85 },
    ]
  },
  {
    title: '🎨 Frontend',
    skills: [
      { name: 'HTML', icon: '📄', level: 80 },
      { name: 'CSS', icon: '🎨', level: 75 },
      { name: 'JavaScript', icon: '⚡', level: 75 },
    ]
  },
  {
    title: '☁️ Cloud & DevOps',
    skills: [
      { name: 'AWS (S3, CloudFront, ECS)', icon: '☁️', level: 60 },
      { name: 'Redis (caching, session, queue)', icon: '🔴', level: 75 },
      { name: 'Docker', icon: '🐳', level: 50 },
    ]
  },
  {
    title: '🛠️ Tools & Other',
    skills: [
      { name: 'Git / GitHub', icon: '📦', level: 85 },
      { name: 'System Design', icon: '🏗️', level: 75 },
      { name: 'AI', icon: '🤖', level: 65 },
    ]
  }
]
</script>

<style scoped>
.reveal-up {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.7s ease, transform 0.7s ease;
}
.reveal-up.visible {
  opacity: 1;
  transform: none;
}
.skills {
  padding: 6rem 2rem;
  background: rgba(255, 255, 255, 0.01);
}
.container {
  max-width: 1200px;
  margin: 0 auto;
}
.section-title {
  text-align: center;
  font-size: 2.2rem;
  font-weight: 700;
  color: #fff;
  margin-bottom: 3rem;
}
.section-title::after {
  content: '';
  display: block;
  width: 60px;
  height: 4px;
  background: linear-gradient(135deg, #6366f1, #8b5cf6);
  margin: 0.8rem auto 0;
  border-radius: 2px;
}
.skills-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 2.5rem;
}
.skill-category {
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.06);
  border-radius: 16px;
  padding: 2rem;
  transition: all 0.3s;
}
.skill-category:hover {
  border-color: rgba(99, 102, 241, 0.2);
  background: rgba(99, 102, 241, 0.03);
}
.skill-category h3 {
  color: #e2e8f0;
  font-size: 1.15rem;
  font-weight: 600;
  margin-bottom: 1.5rem;
}
.skill-items {
  display: flex;
  flex-direction: column;
  gap: 1.2rem;
}
.skill-header {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  margin-bottom: 0.4rem;
}
.skill-icon { font-size: 1.1rem; }
.skill-icon img { width: 1.1rem; height: 1.1rem; vertical-align: middle; }
.skill-name {
  color: #cbd5e1;
  font-size: 0.95rem;
  font-weight: 500;
  flex: 1;
}
.skill-level {
  color: #8b5cf6;
  font-size: 0.85rem;
  font-weight: 600;
  font-family: 'JetBrains Mono', monospace;
}
.skill-bar {
  height: 6px;
  background: rgba(255, 255, 255, 0.06);
  border-radius: 3px;
  overflow: hidden;
}
.skill-bar-fill {
  height: 100%;
  background: linear-gradient(90deg, #6366f1, #8b5cf6, #a78bfa);
  border-radius: 3px;
  transition: width 1.2s cubic-bezier(0.22, 1, 0.36, 1) 0.4s;
}

@media (max-width: 768px) {
  .skills-grid {
    grid-template-columns: 1fr;
  }
}
</style>
