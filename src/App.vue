<script setup>
import { ref } from 'vue'
// Import file CSS yang baru dibuat
import './assets/style.css'

// --- 1. IMPORT ASSETS ---
import profileImg from './assets/images/profile.jpg'
import heroBg from './assets/images/hero-bg.webp'

import proj1Img from './assets/images/projects/project1.jpg'
import proj2Img from './assets/images/projects/project2.jpg'
import proj3Img from './assets/images/projects/project3.jpg'
import proj4Img from './assets/images/projects/project4.jpg'

// --- 2. TECH STACK ICONS (Menggunakan Devicon CDN) ---
const techSkills = ref([
  { name: 'HTML5', url: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/html5/html5-original.svg' },
  { name: 'CSS3', url: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/css3/css3-original.svg' },
  { name: 'Bootstrap', url: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/bootstrap/bootstrap-original.svg' },
  { name: 'JavaScript', url: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/javascript/javascript-original.svg' },
  { name: 'PHP', url: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/php/php-original.svg' },
  { name: 'MySQL', url: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/mysql/mysql-original.svg' },
  { name: 'Laravel', url: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/laravel/laravel-original.svg' },
  { name: 'Vue.js', url: 'https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/vuejs/vuejs-original.svg' }
])

// --- 3. PROJECTS DATA (Translated) ---
const projects = ref([
  {
    id: 1,
    title: 'Packaging Document Approval Workflow',
    desc: 'A digitalized packaging approval workflow system (Paperless Office) built for enterprise business process efficiency at PT Kayaba Indonesia.',
    tech: ['Laravel', 'Vue.js', 'MySQL'],
    link: '#', 
    image: proj1Img
  },
  {
    id: 2,
    title: 'PANDARA Scoring System',
    desc: 'A real-time scoring information system developed specifically for Paskibra competitions, ensuring accurate and transparent results.',
    tech: ['Laravel', 'Livewire', 'Database'],
    link: '#',
    image: proj2Img
  },
  {
    id: 3,
    title: 'E-Report Card System',
    desc: 'An integrated student report card management system designed to help educators streamline grading and academic reporting.',
    tech: ['PHP', 'MySQL', 'Web App'],
    link: '#',
    image: proj3Img
  },
  {
    id: 4,
    title: 'APC Business Management',
    desc: 'An internal e-commerce and inventory management system built to handle daily operations for Atribut Paskibra Cikarang.',
    tech: ['Vue.js', 'Fullstack', 'Business Logic'],
    link: '#',
    image: proj4Img
  }
])

const contact = {
  email: 'abid.azis@example.com',
  linkedin: 'https://linkedin.com/in/abidazis',
  github: 'https://github.com/abidazis',
  cvFile: '/CV_Abid_Azis.pdf' // Sesuaikan dengan nama file CV kamu di folder public
}
</script>

<template>
  <div class="app-wrapper">
    <div class="global-overlay"></div>

    <nav class="navbar">
      <div class="nav-container">
        <span class="logo">Abid<span class="highlight">.</span>Azis</span>
        <div class="nav-links">
          <a href="#projects">Work</a>
          <a :href="contact.github" target="_blank">Git</a>
          <a :href="'mailto:' + contact.email" class="nav-cta">Hire Me</a>
        </div>
      </div>
    </nav>

    <main class="main-content">
      <section class="hero" :style="{ backgroundImage: `url(${heroBg})` }">
        <div class="hero-overlay"></div>
        <div class="container hero-inner">
          <div class="hero-text-block">
            <p class="greeting">Hi, I'm <span class="hand-icon">👋</span></p>
            <h1 class="hero-name gradient-text">Abid Azis</h1>
            <h2 class="hero-title">Information Systems Student | <span class="highlight">Full-Stack Developer</span></h2>
            <p class="hero-bio">
              An Information Systems student at UNSIKA with a strong passion for building efficient digital solutions. 
              Experienced in using <strong>Laravel & Vue.js</strong> to transform conventional business workflows into scalable, user-friendly web applications.
            </p>

            <div class="tech-stack">
              <p class="tech-stack-title">Tech Stack</p>
              <div class="tech-icons">
                <img v-for="skill in techSkills" :key="skill.name" :src="skill.url" :alt="skill.name" :title="skill.name" class="tech-icon-img" />
              </div>
            </div>

            <div class="hero-cta">
              <a :href="contact.cvFile" download class="btn btn-primary">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path><polyline points="7 10 12 15 17 10"></polyline><line x1="12" y1="15" x2="12" y2="3"></line></svg>
                Download CV
              </a>
              <a href="#projects" class="btn btn-secondary">View Work</a>
            </div>
          </div>
          
          <div class="hero-image-block">
            <div class="profile-frame">
              <img :src="profileImg" alt="Abid Azis" class="profile-photo" />
            </div>
          </div>
        </div>
      </section>

      <section id="projects" class="projects">
        <div class="container">
          <div class="section-header">
            <p class="section-tag">Featured Portfolio</p>
            <h2 class="section-title">Selected Works</h2>
            <div class="title-line"></div>
          </div>

          <div class="project-grid">
            <div v-for="item in projects" :key="item.id" class="project-card">
              <div class="card-image-wrapper">
                <img :src="item.image" :alt="item.title" class="card-image" />
                <div class="card-image-overlay">
                  <a v-if="item.link !== '#'" :href="item.link" target="_blank" class="view-link">View Project →</a>
                </div>
              </div>
              
              <div class="card-content">
                <h3 class="card-title">{{ item.title }}</h3>
                <p class="card-desc">{{ item.desc }}</p>
                <div class="tags-wrapper">
                  <span v-for="tech in item.tech" :key="tech" class="tag-pill">{{ tech }}</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </main>

    <footer class="footer">
      <div class="container footer-inner">
        <p class="copyright">© 2026 Abid Azis. Crafted with <span class="vue-icon">V</span> Vue.js & Vite.</p>
        <div class="footer-socials">
          <a :href="'mailto:' + contact.email" title="Email Me">Email</a>
          <a :href="contact.linkedin" target="_blank" title="LinkedIn">LinkedIn</a>
          <a :href="contact.github" target="_blank" title="GitHub">GitHub</a>
        </div>
      </div>
    </footer>
  </div>
</template>

<style scoped>
/* Kosongkan block ini karena CSS sudah dipisah ke src/assets/style.css */
</style>