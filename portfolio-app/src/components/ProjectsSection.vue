<template>
  <section id="projects" class="projects">
    <div class="container">
      <h2 class="section-title reveal-up" ref="titleRef" :class="{ visible: titleVisible }">Projects</h2>
      <div class="projects-grid" ref="gridRef" :class="{ visible: gridVisible }">
        <article v-for="(project, index) in projects" :key="project.title" class="project-card" :style="{ transitionDelay: (index * 0.15) + 's' }">
          <div class="project-icon">{{ project.icon }}</div>
          <div class="project-header">
            <h3>{{ project.title }}</h3>
            <span class="project-period">{{ project.period }}</span>
          </div>
          <p class="project-role">{{ project.role }}</p>
          <p class="project-desc">{{ project.description }}</p>
          <ul class="project-highlights">
            <li v-for="(highlight, i) in project.highlights" :key="i">{{ highlight }}</li>
          </ul>
          <div class="project-tech">
            <span v-for="tech in project.tech" :key="tech" class="tech-tag">{{ tech }}</span>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup>
import { useScrollReveal } from '../composables/useScrollReveal'
const { elementRef: titleRef, isVisible: titleVisible } = useScrollReveal()
const { elementRef: gridRef, isVisible: gridVisible } = useScrollReveal({ threshold: 0.1 })

const projects = [
  {
    icon: '🛒',
    title: 'SBJ Cart',
    period: 'Aug 2023 — Present',
    role: 'Backend Developer · Team of 10–30',
    description: 'APIs for cart management, payment processing, and order information. Extension of the SBJ Online Store project.',
    highlights: [
      'Built SSO login for multi-system admin access',
      'Integrated GMO payment gateway with Star points–based payment and Giftee discount codes',
      'Designed product recommendation engine based on customer purchase analysis',
      'Implemented error logging with CloudWatch and utilized AWS services (S3, CloudFront, Redis, ECS)',
    ],
    tech: ['PHP', 'Laravel', 'Elasticsearch', 'AWS', 'Redis', 'MySQL'],
  },
  {
    icon: '🏪',
    title: 'SBJ Online Store',
    period: 'Feb 2022 — May 2024',
    role: 'Backend Developer · Team of 10–20',
    description: 'Product management and sales website for a globally renowned brand.',
    highlights: [
      'Designed databases for admin information and product details',
      'Utilized Prismatix Elasticsearch to manage product data for e-commerce',
      'Built external vendor API for data reconciliation and matching',
      'Implemented batch processing for data lake with EC2 execution',
    ],
    tech: ['PHP', 'Laravel', 'Elasticsearch', 'MySQL', 'AWS EC2', 'API'],
  },
  {
    icon: '💬',
    title: 'Shabell',
    period: 'Feb 2023 — Jun 2023',
    role: 'Backend Developer · Team of 15',
    description: 'API for a job search application connecting candidates with employers.',
    highlights: [
      'Developed candidate profile creation and job search features',
      'Implemented SQL-based candidate search matching employer criteria',
      'Integrated SSO login with Facebook, Twitter, and Line',
      'Built Twilio SMS API integration for marketing and conversational chat',
    ],
    tech: ['PHP', 'Laravel', 'MySQL', 'Twilio', 'OAuth'],
  },
  {
    icon: '🦄',
    title: 'Unicorn',
    period: 'Jan 2025 — Mar 2025',
    role: 'Backend Developer · Team of 6',
    description: 'Research and upgrade legacy app specifications for the Laravel platform.',
    highlights: [
      'Defined specifications and created architecture documentation',
      'Upgraded Laravel and MySQL for AWS Elastic Beanstalk deployment',
      'Implemented CloudFront for static page caching and server offloading',
      'Prepared deployment documents and transferred to maintenance team',
    ],
    tech: ['PHP', 'Laravel', 'MySQL', 'AWS Beanstalk', 'CloudFront'],
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
.projects-grid .project-card {
  opacity: 0;
  transform: translateY(40px) scale(0.95);
  transition: opacity 0.6s ease, transform 0.6s ease, border-color 0.3s, background 0.3s, box-shadow 0.3s;
}
.projects-grid.visible .project-card {
  opacity: 1;
  transform: none;
}
.projects {
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
.projects-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 2rem;
}
.project-card {
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.06);
  border-radius: 16px;
  padding: 2rem;
  transition: all 0.3s;
  display: flex;
  flex-direction: column;
}
.project-card:hover {
  border-color: rgba(99, 102, 241, 0.3);
  background: rgba(99, 102, 241, 0.03);
  transform: translateY(-4px);
  box-shadow: 0 12px 40px rgba(0, 0, 0, 0.2);
}
.project-icon {
  font-size: 2rem;
  margin-bottom: 1rem;
}
.project-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 0.3rem;
  gap: 0.5rem;
  flex-wrap: wrap;
}
.project-header h3 {
  color: #e2e8f0;
  font-size: 1.2rem;
  font-weight: 700;
}
.project-period {
  color: #64748b;
  font-size: 0.8rem;
  font-family: 'JetBrains Mono', monospace;
  white-space: nowrap;
  background: rgba(99, 102, 241, 0.1);
  padding: 0.2rem 0.6rem;
  border-radius: 20px;
}
.project-role {
  color: #a78bfa;
  font-size: 0.9rem;
  font-weight: 500;
  margin-bottom: 0.8rem;
}
.project-desc {
  color: #94a3b8;
  font-size: 0.95rem;
  line-height: 1.6;
  margin-bottom: 1rem;
}
.project-highlights {
  list-style: none;
  padding: 0;
  margin: 0 0 1.5rem;
  flex: 1;
}
.project-highlights li {
  color: #94a3b8;
  font-size: 0.88rem;
  line-height: 1.6;
  padding-left: 1.2rem;
  position: relative;
  margin-bottom: 0.4rem;
}
.project-highlights li::before {
  content: '▹';
  position: absolute;
  left: 0;
  color: #6366f1;
}
.project-tech {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-top: auto;
}
.tech-tag {
  background: rgba(99, 102, 241, 0.1);
  color: #a78bfa;
  padding: 0.25rem 0.7rem;
  border-radius: 20px;
  font-size: 0.78rem;
  font-family: 'JetBrains Mono', monospace;
  font-weight: 500;
}

@media (max-width: 768px) {
  .projects-grid {
    grid-template-columns: 1fr;
  }
}
</style>
