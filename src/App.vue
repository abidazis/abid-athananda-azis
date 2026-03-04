<script setup>
import { ref } from 'vue'
import './assets/style.css'

// --- 1. IMPORT ASSETS ---
import profileImg from './assets/images/profile.jpg'
import heroBg from './assets/images/hero-bg.webp'

// Import Foto (Pastikan file ini benar-benar ADA di folder kamu)
import proj1Img from './assets/images/projects/project1.jpg'
import proj2Img from './assets/images/projects/project2.jpg'
import proj3Img from './assets/images/projects/project3.jpg'
import proj4Img from './assets/images/projects/project4.jpg'
// Kalau nanti kamu punya foto ke-2 dan ke-3, import juga di sini ya:
// import proj1Img_2 from './assets/images/projects/project1-2.jpg'

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
    title: 'Document Approval Workflow',
    shortDesc: 'A digitalized paperless workflow system for enterprise packaging approvals.',
    fullDesc: 'A comprehensive web-based workflow system built to improve business process efficiency (Paperless Office) at PT Kayaba Indonesia. This system digitizes the manual packaging document approval process, featuring multi-level role approvals, real-time status tracking, and structured digital archiving.',
    tech: ['Laravel', 'Vue.js', 'MySQL', 'System Analysis'],
    link: '#', 
    github: '#',
    // Masukkan variabel gambar yang sudah di-import di atas.
    // Sementara saya isi proj1Img sebanyak 3x agar galerinya tetap terlihat penuh.
    images: [proj1Img, proj1Img, proj1Img] 
  },
  {
    id: 2,
    title: 'Business Travel Management',
    shortDesc: 'A corporate system designed to manage travel documents and requests.',
    fullDesc: 'An internal web application designed to streamline corporate business travel. The system allows employees to submit travel requests, manages the approval hierarchy, calculates estimated travel allowances, and generates official travel assignment letters automatically.',
    tech: ['Laravel', 'Web Development', 'MySQL'],
    link: '#',
    github: '#',
    images: [proj2Img, proj2Img]
  },
  {
    id: 3,
    title: 'Corporate Social Responsibility (CSR) System',
    shortDesc: 'A platform to manage, track, and report corporate social responsibility programs.',
    fullDesc: 'A centralized digital platform created to manage a company’s CSR initiatives. It features budget tracking, program documentation, beneficiary management, and generates comprehensive reports to measure the impact of the social programs implemented.',
    tech: ['Laravel', 'Vue.js', 'UI/UX'],
    link: '#',
    github: '#',
    images: [proj3Img, proj3Img, proj3Img]
  },
  {
    id: 4,
    title: 'DesaGo Market E-Commerce',
    shortDesc: 'An innovative digital marketplace built to empower village economies.',
    fullDesc: 'DesaGo Market is an e-commerce platform dedicated to local village entrepreneurs. It provides a digital storefront for rural products, complete with a shopping cart, order management, and payment gateway integration to help local businesses reach a wider market.',
    tech: ['Fullstack', 'API Integration', 'UI/UX'],
    link: '#',
    github: '#',
    images: [proj4Img, proj4Img]
  },
  {
    id: 5,
    title: 'PANDARA Scoring System',
    shortDesc: 'A real-time scoring and leaderboard system for Paskibra competitions.',
    fullDesc: 'PANDARA is a specialized scoring management system engineered for Paskibra competitions. It eliminates human error by providing judges with a digital scoring interface, automatically calculating complex weightings, and projecting real-time leaderboards for the audience.',
    tech: ['Laravel', 'Livewire', 'Database Design'],
    link: '#',
    github: '#',
    // Perhatikan: karena belum ada proj5Img, saya pakai proj2Img dulu agar tidak error.
    images: [proj2Img, proj2Img] 
  }
])

const contact = {
  email: 'abidathanandaazis@gmail.com',
  linkedin: 'https://www.linkedin.com/in/abid-athananda-azis/',
  github: 'https://github.com/abidazis',
  cvFile: '/CV_Abid_Azis.pdf'
}

// --- 4. MODAL LOGIC (POP-UP) ---
const isModalOpen = ref(false)
const selectedProject = ref(null)

const openModal = (project) => {
  selectedProject.value = project
  isModalOpen.value = true
  document.body.style.overflow = 'hidden' 
}

const closeModal = () => {
  isModalOpen.value = false
  setTimeout(() => { selectedProject.value = null }, 300) 
  document.body.style.overflow = 'auto' 
}
</script>

<template>
  <div class="app-wrapper">
    <div class="global-overlay"></div>

    <nav class="navbar">
      <div class="nav-container">
        <span class="logo">Abid<span class="highlight">.</span> Athananda Azis</span>
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
            <h2 class="hero-title">Fullstack Web Developer | <span class="highlight">Building Scalable Web</span></h2>
            <p class="hero-bio">
              I help businesses grow through modern, fast, and reliable web systems. 
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
                <img :src="item.images[0]" :alt="item.title" class="card-image" />
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
          <div class="modal-gallery">
            <img v-for="(img, idx) in selectedProject.images" :key="idx" :src="img" :alt="selectedProject.title + ' Screenshot ' + (idx+1)" class="modal-gallery-img" />
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