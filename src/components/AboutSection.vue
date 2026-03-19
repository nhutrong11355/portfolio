<template>
  <section id="about" class="about" ref="sectionRef" :class="{ visible: sectionVisible }">
    <div class="container">
      <h2 class="section-title reveal-up">About Me</h2>
      <div class="about-content">
        <div class="about-text reveal-left" ref="textRef" :class="{ visible: textVisible }">
          <p>
            I'm a <strong>Backend Web Developer</strong> with 4+ years of experience specializing in
            <strong>PHP</strong> and the <strong>Laravel</strong> framework, with additional hands-on experience
            in <strong>Node.js</strong>. I have a strong background in database design, system architecture,
            and building scalable e-commerce platforms, including payment gateway integrations.
          </p>
          <p>
            Experienced in working with <strong>AWS services</strong> such as S3, ECS, RDS, and ElastiCache
            to deploy and maintain cloud-based systems. Highly adaptable and eager to learn new programming
            languages or technologies when required.
          </p>
          <p>
            Currently based in <strong>Da Nang, Vietnam</strong> and planning to relocate to
            <strong>Ho Chi Minh City</strong> in April 2026 to pursue new career opportunities
            and professional growth.
          </p>
        </div>
        <div class="about-details stagger-children" ref="cardsRef" :class="{ visible: cardsVisible }">
          <div class="detail-card">
            <div class="detail-icon">🎓</div>
            <h3>Education</h3>
            <p class="detail-main">Duy Tan University</p>
            <p class="detail-sub">Software Technology | 2018 – 2022</p>
            <p class="detail-sub">GPA: 3.40 / 4.0</p>
          </div>
          <div class="detail-card">
            <div class="detail-icon">💼</div>
            <h3>Experience</h3>
            <p class="detail-main">4+ Years</p>
            <p class="detail-sub">Backend Development</p>
            <p class="detail-sub">E-commerce & APIs</p>
          </div>
          <div class="detail-card">
            <div class="detail-icon">🌍</div>
            <h3>Languages</h3>
            <p class="detail-main">English</p>
            <p class="detail-sub">Working Proficiency</p>
            <p class="detail-sub">TOEIC 700</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { useScrollReveal } from '../composables/useScrollReveal'
const { elementRef: sectionRef, isVisible: sectionVisible } = useScrollReveal()
const { elementRef: textRef, isVisible: textVisible } = useScrollReveal({ threshold: 0.2 })
const { elementRef: cardsRef, isVisible: cardsVisible } = useScrollReveal({ threshold: 0.2 })
</script>

<style scoped>
.about.visible .reveal-up {
  opacity: 1;
  transform: none;
}
.reveal-up {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.7s ease, transform 0.7s ease;
}
.reveal-left {
  opacity: 0;
  transform: translateX(-30px);
  transition: opacity 0.7s ease 0.2s, transform 0.7s ease 0.2s;
}
.reveal-left.visible {
  opacity: 1;
  transform: none;
}
.about {
  padding: 6rem 2rem;
  position: relative;
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
  position: relative;
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
.about-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3rem;
  align-items: start;
}
.about-text p {
  color: #94a3b8;
  line-height: 1.8;
  margin-bottom: 1.2rem;
  font-size: 1.05rem;
}
.about-text strong {
  color: #c4b5fd;
}
.about-details {
  display: flex;
  flex-direction: column;
  gap: 1.2rem;
}
.detail-card {
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.06);
  border-radius: 12px;
  padding: 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 0.3rem;
  transition: all 0.3s;
}
.detail-card:hover {
  background: rgba(99, 102, 241, 0.05);
  border-color: rgba(99, 102, 241, 0.2);
  transform: translateX(5px);
}
.detail-icon { font-size: 1.5rem; margin-bottom: 0.3rem; }
.detail-card h3 {
  color: #e2e8f0;
  font-size: 1rem;
  font-weight: 600;
}
.detail-main {
  color: #a78bfa;
  font-weight: 600;
  font-size: 1.05rem;
}
.detail-sub {
  color: #64748b;
  font-size: 0.9rem;
}

@media (max-width: 768px) {
  .about-content {
    grid-template-columns: 1fr;
  }
}
</style>
