<template>
  <section id="hero" class="hero">
    <div class="hero-bg">
      <div class="gradient-orb orb-1"></div>
      <div class="gradient-orb orb-2"></div>
      <div class="grid-overlay"></div>
    </div>
    <div class="hero-content" ref="elementRef" :class="{ visible: isVisible }">
      <div class="hero-text">
        <p class="hero-greeting animate-item">Hello, I'm</p>
        <h1 class="hero-name animate-item">Nguyen Nhu Trong</h1>
        <h2 class="hero-title animate-item">Software Engineer</h2>
        <p class="hero-desc">
          Backend developer with 4+ years of experience specializing in PHP, Laravel, and cloud-based solutions.
          Passionate about building scalable e-commerce platforms and robust APIs.
        </p>
        <div class="hero-cta">
          <a href="#projects" class="btn btn-primary">View Projects</a>
          <a href="#contact" class="btn btn-outline">Get In Touch</a>
        </div>
        <div class="hero-social">
          <a href="mailto:nguyennhutrong69@gmail.com" aria-label="Email" title="Email">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="2" y="4" width="20" height="16" rx="2"/><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"/></svg>
          </a>
          <a href="https://github.com/nguyennhutrong" target="_blank" rel="noopener" aria-label="GitHub" title="GitHub">
            <svg viewBox="0 0 24 24" fill="currentColor"><path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg>
          </a>
          <a href="tel:0948847448" aria-label="Phone" title="Phone">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"/></svg>
          </a>
        </div>
      </div>
      <div class="hero-image">
        <div class="image-wrapper">
          <img :src="profileImg" alt="Nguyen Nhu Trong" />
        </div>
      </div>
    </div>
    <div class="scroll-indicator">
      <span></span>
    </div>
  </section>
</template>

<script setup>
import profileImg from '../assets/profile.png'
import { useScrollReveal } from '../composables/useScrollReveal'
const { elementRef, isVisible } = useScrollReveal({ threshold: 0.1 })
</script>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  overflow: hidden;
  padding: 6rem 2rem 2rem;
}
.hero-bg {
  position: absolute;
  inset: 0;
  z-index: 0;
}
.gradient-orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(80px);
  opacity: 0.3;
}
.orb-1 {
  width: 500px;
  height: 500px;
  background: #6366f1;
  top: -10%;
  right: -5%;
  animation: float 8s ease-in-out infinite;
}
.orb-2 {
  width: 400px;
  height: 400px;
  background: #8b5cf6;
  bottom: -10%;
  left: -5%;
  animation: float 10s ease-in-out infinite reverse;
}
.grid-overlay {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(rgba(255,255,255,0.03) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255,255,255,0.03) 1px, transparent 1px);
  background-size: 60px 60px;
}
@keyframes float {
  0%, 100% { transform: translate(0, 0); }
  50% { transform: translate(30px, -30px); }
}
.hero-content {
  max-width: 1200px;
  width: 100%;
  margin: 0 auto;
  display: flex;
  align-items: center;
  gap: 4rem;
  position: relative;
  z-index: 1;
}
.hero-text { flex: 1; }
.hero-greeting {
  font-size: 1.1rem;
  color: #8b5cf6;
  font-weight: 500;
  margin-bottom: 0.5rem;
  letter-spacing: 0.05em;
}
.hero-name {
  font-size: clamp(2.5rem, 5vw, 3.5rem);
  font-weight: 800;
  color: #fff;
  line-height: 1.1;
  margin-bottom: 0.5rem;
}
.hero-title {
  font-size: clamp(1.2rem, 2.5vw, 1.6rem);
  font-weight: 500;
  background: linear-gradient(135deg, #6366f1, #a78bfa);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 1.5rem;
}
.hero-desc {
  color: #94a3b8;
  line-height: 1.7;
  font-size: 1.05rem;
  max-width: 520px;
  margin-bottom: 2rem;
}
.hero-cta {
  display: flex;
  gap: 1rem;
  margin-bottom: 2rem;
  flex-wrap: wrap;
}
.btn {
  padding: 0.8rem 1.8rem;
  border-radius: 8px;
  font-weight: 600;
  text-decoration: none;
  font-size: 0.95rem;
  transition: all 0.3s;
  display: inline-block;
}
.btn-primary {
  background: linear-gradient(135deg, #6366f1, #8b5cf6);
  color: #fff;
  box-shadow: 0 4px 15px rgba(99, 102, 241, 0.3);
}
.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(99, 102, 241, 0.4);
}
.btn-outline {
  border: 2px solid rgba(139, 92, 246, 0.5);
  color: #a78bfa;
}
.btn-outline:hover {
  background: rgba(139, 92, 246, 0.1);
  border-color: #8b5cf6;
  transform: translateY(-2px);
}
.hero-social {
  display: flex;
  gap: 1rem;
}
.hero-social a {
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 8px;
  background: rgba(255, 255, 255, 0.05);
  color: #94a3b8;
  transition: all 0.3s;
}
.hero-social a:hover {
  background: rgba(99, 102, 241, 0.2);
  color: #a78bfa;
  transform: translateY(-2px);
}
.hero-social svg { width: 20px; height: 20px; }
.hero-image {
  flex: 0 0 auto;
}
.image-wrapper {
  width: 320px;
  height: 320px;
  border-radius: 20px;
  overflow: hidden;
  border: 3px solid rgba(139, 92, 246, 0.3);
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
  position: relative;
}
.image-wrapper::before {
  content: '';
  position: absolute;
  inset: -3px;
  border-radius: 22px;
  background: linear-gradient(135deg, #6366f1, #8b5cf6, #6366f1);
  z-index: -1;
  animation: borderRotate 4s linear infinite;
}
/* Hero entrance animations */
.hero-content .animate-item,
.hero-content .hero-desc,
.hero-content .hero-cta,
.hero-content .hero-social {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.6s ease, transform 0.6s ease;
}
.hero-content.visible .animate-item,
.hero-content.visible .hero-desc,
.hero-content.visible .hero-cta,
.hero-content.visible .hero-social {
  opacity: 1;
  transform: none;
}
.hero-content.visible .hero-greeting { transition-delay: 0.1s; }
.hero-content.visible .hero-name { transition-delay: 0.2s; }
.hero-content.visible .hero-title { transition-delay: 0.35s; }
.hero-content.visible .hero-desc { transition-delay: 0.5s; }
.hero-content.visible .hero-cta { transition-delay: 0.65s; }
.hero-content.visible .hero-social { transition-delay: 0.8s; }

.hero-image {
  opacity: 0;
  transform: translateX(50px) scale(0.9);
  transition: opacity 0.8s ease 0.3s, transform 0.8s ease 0.3s;
}
.hero-content.visible .hero-image {
  opacity: 1;
  transform: none;
}

@keyframes borderRotate {
  0% { filter: hue-rotate(0deg); }
  100% { filter: hue-rotate(360deg); }
}
.image-wrapper img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.scroll-indicator {
  position: absolute;
  bottom: 2rem;
  left: 50%;
  transform: translateX(-50%);
}
.scroll-indicator span {
  display: block;
  width: 24px;
  height: 40px;
  border-radius: 12px;
  border: 2px solid rgba(139, 92, 246, 0.4);
  position: relative;
}
.scroll-indicator span::after {
  content: '';
  width: 4px;
  height: 8px;
  background: #8b5cf6;
  border-radius: 2px;
  position: absolute;
  top: 6px;
  left: 50%;
  transform: translateX(-50%);
  animation: scrollAnim 2s ease-in-out infinite;
}
@keyframes scrollAnim {
  0% { opacity: 1; top: 6px; }
  100% { opacity: 0; top: 22px; }
}

@media (max-width: 768px) {
  .hero-content {
    flex-direction: column-reverse;
    text-align: center;
    gap: 2rem;
  }
  .hero-desc { margin-left: auto; margin-right: auto; }
  .hero-cta { justify-content: center; }
  .hero-social { justify-content: center; }
  .image-wrapper { width: 220px; height: 220px; }
}
</style>
