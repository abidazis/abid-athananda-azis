<script setup>
import { ref } from 'vue'
import './assets/style.css'

// --- 1. IMPORT ASSETS ---
import profileImg from './assets/images/profile.jpg'
import heroBg from './assets/images/hero-bg.webp'

import proj1Img from './assets/images/projects/project1.jpg'
import proj2Img from './assets/images/projects/project2.jpg'
import proj3Img from './assets/images/projects/project3.jpg'
import proj4Img from './assets/images/projects/project4.jpg'

// --- 2. TECH STACK ICONS ---
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

// --- 3. PROJECTS DATA ---
const projects = ref([
  {
    id: 1,
    title: 'Packaging Document Approval Workflow',
    shortDesc: 'A digitalized packaging approval workflow system (Paperless Office).',
    fullDesc: 'A comprehensive web-based workflow system built for enterprise business process efficiency at PT Kayaba Indonesia. This system digitizes the manual packaging approval process into a paperless, trackable, and efficient workflow. Features include multi-level role approvals, real-time status tracking, and automated email notifications.',
    tech: ['Laravel', 'Vue.js', 'MySQL', 'System Analysis'],
    link: '#', 
    github: '#',
    image: proj1Img
  },
  {
    id: 2,
    title: 'PANDARA Scoring System',
    shortDesc: 'A real-time scoring information system developed for Paskibra competitions.',
    fullDesc: 'PANDARA is a dedicated scoring management system designed to streamline judging in Paskibra competitions. It features real-time leaderboard updates, secure judge authentication, automated calculation algorithms to prevent human error, and comprehensive printable reporting.',
    tech: ['Laravel', 'Livewire', 'MySQL'],
    link: '#',
    github: '#',
    image: proj2Img
  },
  {
    id: 3,
    title: 'E-Report Card System',
    shortDesc: 'An integrated student report card management system.',
    fullDesc: 'An educational platform designed to help teachers manage student grades, attendance, and extracurricular activities. The system automatically calculates final scores and generates formatted report cards (E-Rapor) ready for printing or digital distribution to parents.',
    tech: ['PHP', 'MySQL', 'Bootstrap'],
    link: '#',
    github: '#',
    image: proj3Img
  },
  {
    id: 4,
    title: 'APC Business Management',
    shortDesc: 'An internal e-commerce and inventory management system.',
    fullDesc: 'A custom ERP and e-commerce solution built for Atribut Paskibra Cikarang. It handles daily business operations including inventory tracking, point of sales (cashier), custom product orders (like t-shirt printing), and online portfolio display for customers.',
    tech: ['Vue.js', 'Laravel', 'Tailwind CSS'],
    link: '#',
    github: '#',
    image: proj4Img
  }
])

const contact = {
  email: 'abid.azis@example.com', // Ganti dengan email asli
  linkedin: 'https://linkedin.com/in/abidazis', // Ganti
  github: 'https://github.com/abidazis', // Ganti
  cvFile: '/CV_Abid_Azis.pdf' // NAMA FILE HARUS SAMA PERSIS DENGAN YANG DI FOLDER PUBLIC
}

// --- 4. MODAL LOGIC (POP-UP) ---
const isModalOpen = ref(false)
const selectedProject = ref(null)

const openModal = (project) => {
  selectedProject.value = project
  isModalOpen.value = true
  document.body.style.overflow = 'hidden' // Kunci scroll halaman belakang
}

const closeModal = () => {
  isModalOpen.value = false
  setTimeout(() => { selectedProject.value = null }, 300) // Delay hapus data biar animasi smooth
  document.body.style.overflow = 'auto' // Buka kunci scroll
}
</script>

<template>
  <div class="app-wrapper">
    <div class="global-overlay"></div>

    <nav class="navbar">
      <div class="nav-container">
        <span class="logo">Abid<span class="highlight">.</span>Azis</span>
        <div class="nav-links">
          <a href="#skills">Skills</a>
          <a href="#projects">Work</a>
          <a :href="contact.github" target="_blank">Git</a>
          <a href="#cta" class="nav-cta">Hire Me</a>
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

            <div class="hero-cta">
              <a :href="contact.cvFile" download target="_blank" class="btn btn-primary">
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

      <section id="skills" class="skills-section">
        <div class="container">
          <div class="section-header text-center">
            <p class="section-tag">My Arsenal</p>
            <h2 class="section-title">Tech Stack & Tools</h2>
            <div class="title-line mx-auto"></div>
          </div>
          
          <div class="tech-grid">
            <div v-for="skill in techSkills" :key="skill.name" class="tech-card">
              <img :src="skill.url" :alt="skill.name" class="tech-icon-large" />
              <p class="tech-name">{{ skill.name }}</p>
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
            <div v-for="item in projects" :key="item.id" class="project-card" @click="openModal(item)">
              <div class="card-image-wrapper">
                <img :src="item.image" :alt="item.title" class="card-image" />
                <div class="card-image-overlay">
                  <span class="view-link">View Details 🔍</span>
                </div>
              </div>
              
              <div class="card-content">
                <h3 class="card-title">{{ item.title }}</h3>
                <p class="card-desc">{{ item.shortDesc }}</p>
                <div class="tags-wrapper">
                  <span v-for="tech in item.tech.slice(0,3)" :key="tech" class="tag-pill">{{ tech }}</span>
                  <span v-if="item.tech.length > 3" class="tag-pill">+{{ item.tech.length - 3 }}</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section id="cta" class="cta-section">
        <div class="container cta-container">
          <h2 class="cta-title">Let's Build Something Amazing Together.</h2>
          <p class="cta-desc">I am currently open for full-time opportunities, internships, or freelance projects. Let's discuss how my skills can bring value to your team.</p>
          <div class="cta-buttons">
            <a :href="'mailto:' + contact.email" class="btn btn-primary cta-btn">
              <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"></path><polyline points="22,6 12,13 2,6"></polyline></svg>
              Send me an Email
            </a>
            <a :href="contact.linkedin" target="_blank" class="btn btn-secondary cta-btn">Connect on LinkedIn</a>
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

    <div v-if="isModalOpen" class="modal-overlay" @click.self="closeModal">
      <div class="modal-content">
        <button class="close-btn" @click="closeModal">×</button>
        
        <div v-if="selectedProject" class="modal-body">
          <div class="modal-image-container">
            <img :src="selectedProject.image" :alt="selectedProject.title" class="modal-image" />
          </div>
          
          <div class="modal-info">
            <h2 class="modal-title">{{ selectedProject.title }}</h2>
            
            <div class="modal-tags">
              <span v-for="tech in selectedProject.tech" :key="tech" class="tag-pill accent-pill">{{ tech }}</span>
            </div>
            
            <div class="modal-desc">
              <h3>About the Project</h3>
              <p>{{ selectedProject.fullDesc }}</p>
            </div>
            
            <div class="modal-actions">
              <a v-if="selectedProject.link !== '#'" :href="selectedProject.link" target="_blank" class="btn btn-primary btn-sm">Live Demo ↗</a>
              <a v-if="selectedProject.github !== '#'" :href="selectedProject.github" target="_blank" class="btn btn-secondary btn-sm">Source Code</a>
            </div>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<style scoped>
/* Kosong karena style diatur di style.css */
</style>