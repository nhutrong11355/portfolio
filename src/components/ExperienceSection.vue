<template>
  <section id="experience" class="experience">
    <div class="container">
      <h2 class="section-title reveal-up" ref="titleRef" :class="{ visible: titleVisible }">Work Experience</h2>
      <div class="timeline" ref="timelineRef" :class="{ visible: timelineVisible }">
        <div v-for="(job, index) in jobs" :key="index" class="timeline-item" :style="{ transitionDelay: (index * 0.2) + 's' }">
          <div class="timeline-marker"></div>
          <div class="timeline-content">
            <div class="timeline-header">
              <div>
                <h3>{{ job.title }}</h3>
                <p class="company">{{ job.company }}</p>
              </div>
              <span class="timeline-date">{{ job.period }}</span>
            </div>
            <p class="description" v-if="job.description">{{ job.description }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { useScrollReveal } from '../composables/useScrollReveal'
const { elementRef: titleRef, isVisible: titleVisible } = useScrollReveal()
const { elementRef: timelineRef, isVisible: timelineVisible } = useScrollReveal({ threshold: 0.2 })

const jobs = [
  {
    title: 'Software Engineer',
    company: 'VNPT-media',
    period: 'Jun 2026 — Present',
    description: 'Backend Developer responsible for developing telecommunications service applications using a microservices architecture.'
  },
  {
    title: 'Software Engineer',
    company: 'SupremeTech',
    period: 'Jun 2023 — Apr 2026',
    description: 'Leading backend development for e-commerce platforms including SBJ Cart. Building APIs for cart management, payment processing (GMO gateway, Star points-based payments), SSO login, and product recommendation systems. Working with AWS services (S3, CloudFront, Redis, ECS) and Elasticsearch.'
  },
  {
    title: 'Associate Software Engineer',
    company: 'SupremeTech',
    period: 'Feb 2022 — Jun 2023',
    description: 'Developed backend services for SBJ Online Store and Shabell projects. Designed databases, built APIs for external vendor data reconciliation, implemented Elasticsearch for product data, and built batch processing pipelines for data lake integration.'
  },
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
.timeline .timeline-item {
  opacity: 0;
  transform: translateX(-30px);
  transition: opacity 0.6s ease, transform 0.6s ease;
}
.timeline.visible .timeline-item {
  opacity: 1;
  transform: none;
}
.timeline::before {
  transform-origin: top;
  transform: scaleY(0);
  transition: transform 0.8s ease;
}
.timeline.visible::before {
  transform: scaleY(1);
}
.experience {
  padding: 6rem 2rem;
}
.container {
  max-width: 900px;
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
.timeline {
  position: relative;
  padding-left: 2rem;
}
.timeline::before {
  content: '';
  position: absolute;
  left: 7px;
  top: 0;
  bottom: 0;
  width: 2px;
  background: linear-gradient(180deg, #6366f1, rgba(99, 102, 241, 0.1));
}
.timeline-item {
  position: relative;
  margin-bottom: 2.5rem;
}
.timeline-item:last-child { margin-bottom: 0; }
.timeline-marker {
  position: absolute;
  left: -2rem;
  top: 0.3rem;
  width: 16px;
  height: 16px;
  border-radius: 50%;
  background: #0f172a;
  border: 3px solid #6366f1;
  z-index: 1;
}
.timeline-item:first-child .timeline-marker {
  background: #6366f1;
  box-shadow: 0 0 15px rgba(99, 102, 241, 0.5);
}
.timeline-content {
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.06);
  border-radius: 12px;
  padding: 1.5rem 2rem;
  transition: all 0.3s;
}
.timeline-content:hover {
  border-color: rgba(99, 102, 241, 0.2);
  background: rgba(99, 102, 241, 0.03);
  transform: translateX(5px);
}
.timeline-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 0.8rem;
  gap: 1rem;
  flex-wrap: wrap;
}
.timeline-header h3 {
  color: #e2e8f0;
  font-size: 1.15rem;
  font-weight: 600;
}
.company {
  color: #a78bfa;
  font-weight: 500;
  font-size: 0.95rem;
}
.timeline-date {
  color: #64748b;
  font-size: 0.85rem;
  font-family: 'JetBrains Mono', monospace;
  white-space: nowrap;
  background: rgba(99, 102, 241, 0.1);
  padding: 0.25rem 0.75rem;
  border-radius: 20px;
}
.description {
  color: #94a3b8;
  line-height: 1.7;
  font-size: 0.95rem;
}

@media (max-width: 768px) {
  .timeline-header {
    flex-direction: column;
  }
}
</style>
