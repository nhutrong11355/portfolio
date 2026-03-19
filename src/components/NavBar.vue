<template>
  <nav class="navbar" :class="{ scrolled: isScrolled }">
    <div class="nav-container">
      <a href="#hero" class="nav-logo">NT</a>
      <button class="nav-toggle" @click="toggleMenu" :aria-label="menuOpen ? 'Close menu' : 'Open menu'">
        <span :class="{ open: menuOpen }"></span>
      </button>
      <ul class="nav-links" :class="{ active: menuOpen }">
        <li v-for="link in links" :key="link.href">
          <a :href="link.href" @click="closeMenu">{{ link.label }}</a>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const menuOpen = ref(false)

const links = [
  { href: '#about', label: 'About' },
  { href: '#skills', label: 'Skills' },
  { href: '#experience', label: 'Experience' },
  { href: '#projects', label: 'Projects' },
  { href: '#contact', label: 'Contact' },
]

const toggleMenu = () => { menuOpen.value = !menuOpen.value }
const closeMenu = () => { menuOpen.value = false }

const handleScroll = () => { isScrolled.value = window.scrollY > 50 }

onMounted(() => window.addEventListener('scroll', handleScroll))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  padding: 1rem 0;
  transition: all 0.3s ease;
  background: transparent;
}
.navbar.scrolled {
  background: rgba(15, 23, 42, 0.95);
  backdrop-filter: blur(10px);
  padding: 0.6rem 0;
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.15);
}
.nav-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.nav-logo {
  font-size: 1.5rem;
  font-weight: 800;
  color: #fff;
  text-decoration: none;
  background: linear-gradient(135deg, #6366f1, #8b5cf6);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
.nav-links {
  display: flex;
  list-style: none;
  gap: 2rem;
  margin: 0;
  padding: 0;
}
.nav-links a {
  color: #cbd5e1;
  text-decoration: none;
  font-weight: 500;
  font-size: 0.95rem;
  transition: color 0.3s;
  position: relative;
}
.nav-links a::after {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 0;
  width: 0;
  height: 2px;
  background: linear-gradient(135deg, #6366f1, #8b5cf6);
  transition: width 0.3s;
}
.nav-links a:hover { color: #fff; }
.nav-links a:hover::after { width: 100%; }
.nav-toggle {
  display: none;
  background: none;
  border: none;
  cursor: pointer;
  padding: 0.5rem;
}
.nav-toggle span,
.nav-toggle span::before,
.nav-toggle span::after {
  display: block;
  width: 24px;
  height: 2px;
  background: #fff;
  transition: all 0.3s;
  position: relative;
}
.nav-toggle span::before,
.nav-toggle span::after {
  content: '';
  position: absolute;
}
.nav-toggle span::before { top: -7px; }
.nav-toggle span::after { top: 7px; }
.nav-toggle span.open { background: transparent; }
.nav-toggle span.open::before { top: 0; transform: rotate(45deg); }
.nav-toggle span.open::after { top: 0; transform: rotate(-45deg); }

@media (max-width: 768px) {
  .nav-toggle { display: block; }
  .nav-links {
    position: fixed;
    top: 0;
    right: -100%;
    width: 70%;
    height: 100vh;
    flex-direction: column;
    background: rgba(15, 23, 42, 0.98);
    padding: 5rem 2rem 2rem;
    transition: right 0.3s ease;
    gap: 1.5rem;
  }
  .nav-links.active { right: 0; }
  .nav-links a { font-size: 1.1rem; }
}
</style>
