<script setup>
import { ref } from 'vue'

// --- 1. IMPORT ASSETS (Pastikan file ada di folder src/assets/images/) ---
// Foto Profil & Background
import profileImg from './assets/images/profile.jpg'
import heroBg from './assets/images/hero-bg.webp'

// Gambar Proyek (sesuaikan nama file dengan yang kamu letakkan di folder src/assets/images/projects/)
import proj1Img from './assets/images/projects/project1.jpg'
import proj2Img from './assets/images/projects/project2.jpg'
import proj3Img from './assets/images/projects/project3.jpg'
import proj4Img from './assets/images/projects/project4.jpg'

// --- 2. DATA PROJEK ---
const projects = ref([
  {
    id: 1,
    title: 'Sistem Digitalisasi CSR',
    desc: 'Aplikasi pengelolaan Corporate Social Responsibility berbasis web untuk korporasi.',
    tech: ['Laravel', 'Vue.js', 'MySQL', 'UI/UX'],
    link: '#', // Ganti dengan link live/repo
    image: proj1Img // Memakai hasil import gambar
  },
  {
    id: 2,
    title: 'DesaGo Market',
    desc: 'Platform marketplace inovatif untuk pemberdayaan ekonomi desa.',
    tech: ['Web Dev', 'API Integration', 'UI/UX'],
    link: '#',
    image: proj2Img
  },
  {
    id: 3,
    title: 'Digital Packaging Approval',
    desc: 'Sistem digitalisasi formulir persetujuan kemasan (Paperless Office) untuk efisiensi.',
    tech: ['System Analysis', 'Backend', 'Web App'],
    link: '#',
    image: proj3Img
  },
  {
    id: 4,
    title: 'Atribut Paskibra Cikarang',
    desc: 'Pengembangan sistem manajemen bisnis dan portofolio e-commerce terintegrasi.',
    tech: ['Business Logic', 'Fullstack', 'Web Dev'],
    link: '#',
    image: proj4Img
  }
])

const contact = {
  email: 'abid.azis.dev@example.com', // GANTI INI
  linkedin: 'https://linkedin.com/in/abidazis', // GANTI INI
  github: 'https://github.com/abidazis' // GANTI INI
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
            <p class="greeting">Halo, Saya <span class="hand-icon">👋</span></p>
            <h1 class="hero-name gradient-text">Abid Azis</h1>
            <h2 class="hero-title">Information Systems Student | <span class="highlight">Full-Stack Web Developer</span></h2>
            <p class="hero-bio">
              Mahasiswa semester 7 yang fokus membangun solusi digital efisien menggunakan 
              <strong>Laravel & Vue.js</strong>. Berpengalaman mengubah sistem konvensional 
              menjadi aplikasi web yang *scalable* dan *user-friendly*.
            </p>
            <div class="hero-cta">
              <a href="#projects" class="btn btn-primary">Lihat Karya</a>
              <a :href="contact.linkedin" target="_blank" class="btn btn-secondary">LinkedIn Profile</a>
            </div>
          </div>
          <div class="hero-image-block">
            <div class="profile-frame">
              <img :src="profileImg" alt="Abid Azis - Web Developer" class="profile-photo" />
            </div>
          </div>
        </div>
      </section>

      <section id="projects" class="projects">
        <div class="container">
          <div class="section-header">
            <p class="section-tag">Featured Work</p>
            <h2 class="section-title">Proyek Unggulan</h2>
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
          <a :href="contact.email" title="Email Saya">Email</a>
          <a :href="contact.linkedin" target="_blank" title="LinkedIn">LiN</a>
          <a :href="contact.github" target="_blank" title="GitHub">Git</a>
        </div>
      </div>
    </footer>
  </div>
</template>

<style>
/* --- A. GLOBAL RESET & FOUNDATION --- */
:root {
  /* Palette Warna Modern (Dark) */
  --bg-dark: #0a0e17;        /* Latar belakang utama super gelap */
  --bg-card: #141a29;        /* Latar belakang card/elemen */
  --accent: #42b883;         /* Vue Green */
  --accent-secondary: #35495e; /* Vue Dark Blue */
  
  --text-main: #f4f4f7;
  --text-muted: #9ca3af;
  
  --shadow-card: 0 10px 30px -10px rgba(2,12,27,0.7);
  
  /* Font Family */
  --font-main: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
}

* { box-sizing: border-box; margin: 0; padding: 0; }

html { scroll-behavior: smooth; }

body { 
  background-color: var(--bg-dark); 
  color: var(--text-main); 
  font-family: var(--font-main); 
  line-height: 1.6; 
  overflow-x: hidden; 
}

a { text-decoration: none; color: inherit; transition: 0.3s; }

.container { max-width: 1200px; margin: 0 auto; padding: 0 30px; }
.highlight { color: var(--accent); }

/* Efek Gradient Text (Kunci Desain Modern) */
.gradient-text {
  background: linear-gradient(135deg, #f4f4f7 30%, var(--accent) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  color: transparent; /* fallback */
}

/* --- B. APPS WRAPPER & OVERLAYS --- */
.app-wrapper { position: relative; min-height: 100vh; }
.global-overlay {
  position: fixed; top: 0; left: 0; width: 100%; height: 100%;
  background-image: radial-gradient(rgba(66, 184, 131, 0.05) 1px, transparent 1px);
  background-size: 30px 30px;
  pointer-events: none;
  z-index: -1;
}

/* --- C. NAVBAR (HEADER) --- */
.navbar {
  position: fixed; top: 0; width: 100%; 
  background: rgba(10, 14, 23, 0.8); 
  backdrop-filter: blur(10px); /* Efek Glassmorphism */
  border-bottom: 1px solid rgba(255,255,255,0.05);
  z-index: 1000;
}

.nav-container {
  max-width: 1400px; margin: 0 auto; 
  padding: 20px 40px; 
  display: flex; justify-content: space-between; align-items: center;
}

.logo { font-size: 1.5rem; font-weight: 800; letter-spacing: -1px; }

.nav-links { display: flex; gap: 30px; align-items: center; }
.nav-links a { font-size: 0.95rem; font-weight: 500; color: var(--text-muted); }
.nav-links a:hover { color: var(--accent); }

.nav-cta {
  border: 2px solid var(--accent);
  padding: 8px 18px;
  border-radius: 4px;
  color: var(--accent) !important;
  font-weight: 600 !important;
}
.nav-cta:hover { background: rgba(66, 184, 131, 0.1); transform: translateY(-2px); }

/* --- D. HERO SECTION --- */
.hero {
  min-height: 100vh;
  background-size: cover; background-position: center; background-attachment: fixed;
  position: relative;
  display: flex; align-items: center;
  padding-top: 100px; /* offset navbar */
}

.hero-overlay {
  position: absolute; top: 0; left: 0; width: 100%; height: 100%;
  background: linear-gradient(to bottom, rgba(10, 14, 23, 0.6) 0%, var(--bg-dark) 100%);
}

.hero-inner {
  position: relative; z-index: 10;
  display: grid;
  /* Gunakan minmax agar teks dan gambar tidak saling dorong */
  grid-template-columns: minmax(0, 1.2fr) minmax(0, 0.8fr);
  gap: 40px; 
  align-items: center;
}

.greeting { font-family: 'Courier New', monospace; color: var(--accent); font-size: 1.1rem; margin-bottom: 10px; }
.hand-icon { display: inline-block; animation: wave 2.5s infinite; transform-origin: 70% 70%; }

.hero-name { font-size: 5rem; font-weight: 900; line-height: 1; margin-bottom: 15px; letter-spacing: -3px; }
.hero-title { font-size: 1.6rem; color: var(--text-muted); font-weight: 500; margin-bottom: 25px; }
.hero-bio { max-width: 650px; color: #bdc3c7; font-size: 1.1rem; margin-bottom: 40px; line-height: 1.8; }

/* Buttons */
.hero-cta { display: flex; gap: 20px; }
.btn {
  padding: 15px 35px; border-radius: 6px; font-weight: 700; font-size: 1rem;
  text-transform: uppercase; letter-spacing: 1px;
}
.btn-primary {
  background: var(--accent); color: #0a0e17;
  border: 2px solid var(--accent);
}
.btn-primary:hover { box-shadow: 0 0 20px rgba(66, 184, 131, 0.5); transform: translateY(-3px); }

.btn-secondary {
  border: 2px solid rgba(255,255,255,0.2);
  color: #f4f4f7;
}
.btn-secondary:hover { border-color: var(--accent); background: rgba(66, 184, 131, 0.05); }

/* Profile Photo Frame */
.hero-image-block { 
  display: flex; 
  justify-content: center; /* Ubah jadi center agar seimbang */
  width: 100%;
}

.profile-frame {
  width: 100%;             /* Berubah jadi persentase */
  max-width: 380px;        /* Batas maksimal lebar */
  aspect-ratio: 1 / 1;     /* Otomatis menjaga bentuk bulat sempurna */
  height: auto;            /* Hapus tinggi fixed */
  padding: 15px;
  background: rgba(255,255,255,0.03);
  border: 1px solid rgba(255,255,255,0.08);
  border-radius: 50%;
  backdrop-filter: blur(5px);
  box-shadow: 0 20px 50px rgba(0,0,0,0.4);
}
.profile-photo {
  width: 100%; height: 100%;
  object-fit: cover;
  border-radius: 50%;
  border: 4px solid var(--bg-dark);
}

/* --- E. PROJECTS SECTION --- */
.projects { padding: 120px 0; }

.section-header { text-align: center; margin-bottom: 80px; }
.section-tag { font-family: 'Courier New', monospace; color: var(--accent); font-size: 1rem; text-transform: uppercase; letter-spacing: 3px; }
.section-title { font-size: 3.5rem; font-weight: 900; letter-spacing: -2px; margin: 10px 0 20px; }
.title-line { width: 80px; height: 4px; background: var(--accent); margin: 0 auto; border-radius: 2px; }

/* Project Grid */
.project-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  gap: 40px;
}

/* Project Card (Glassmorphism + Shadow) */
.project-card {
  background: var(--bg-card);
  border: 1px solid rgba(255,255,255,0.03);
  border-radius: 12px;
  overflow: hidden;
  box-shadow: var(--shadow-card);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}
.project-card:hover {
  transform: translateY(-10px) scale(1.02);
  box-shadow: 0 25px 60px -15px rgba(2, 12, 27, 0.8);
  border-color: rgba(66, 184, 131, 0.2);
}

/* Card Image & Hover Effect */
.card-image-wrapper { position: relative; width: 100%; height: 220px; overflow: hidden; }
.card-image { width: 100%; height: 100%; object-fit: cover; transition: transform 0.5s ease; }
.project-card:hover .card-image { transform: scale(1.1); }

.card-image-overlay {
  position: absolute; top: 0; left: 0; width: 100%; height: 100%;
  background: rgba(10, 14, 23, 0.8);
  backdrop-filter: blur(4px);
  display: flex; justify-content: center; align-items: center;
  opacity: 0; transition: opacity 0.3s ease;
}
.card-image-wrapper:hover .card-image-overlay { opacity: 1; }

.view-link {
  color: var(--accent); font-weight: 700; font-size: 1.1rem;
  padding: 10px 20px; border: 2px solid var(--accent); border-radius: 4px;
}

/* Card Content */
.card-content { padding: 30px; }
.card-title { font-size: 1.6rem; font-weight: 700; color: #f4f4f7; margin-bottom: 12px; letter-spacing: -0.5px; }
.card-desc { font-size: 0.95rem; color: #a0a0a0; margin-bottom: 25px; line-height: 1.7; min-height: 65px; }

/* Tags Pills */
.tags-wrapper { display: flex; flex-wrap: wrap; gap: 10px; }
.tag-pill {
  background: #1e293b; color: #f4f4f7;
  font-size: 0.75rem; font-weight: 600; font-family: 'Courier New', monospace;
  padding: 5px 12px; border-radius: 20px;
  border: 1px solid rgba(255,255,255,0.05);
}

/* --- F. FOOTER --- */
.footer {
  background: #080b12;
  padding: 40px 0;
  border-top: 1px solid rgba(255,255,255,0.03);
}
.footer-inner { display: flex; justify-content: space-between; align-items: center; color: var(--text-muted); font-size: 0.85rem; }

.vue-icon { color: var(--accent); font-weight: 900; font-family: cursive; }

.footer-socials { display: flex; gap: 20px; }
.footer-socials a:hover { color: var(--accent); }

/* --- G. KEYFRAMES & RESPONSIVE --- */
@keyframes wave {
  0% { transform: rotate( 0.0deg) }
 10% { transform: rotate(14.0deg) }
 20% { transform: rotate(-8.0deg) }
 30% { transform: rotate(14.0deg) }
 40% { transform: rotate(-4.0deg) }
 50% { transform: rotate(10.0deg) }
 60% { transform: rotate( 0.0deg) }
100% { transform: rotate( 0.0deg) }
}

@media (max-width: 1024px) {
  /* Di layar laptop biasa/tablet, langsung ubah jadi 1 kolom (atas bawah) */
  .hero-inner { 
    grid-template-columns: 1fr; 
    text-align: center; 
    justify-items: center; 
    gap: 40px; 
  }
  .hero-name { font-size: 4rem; letter-spacing: -2px; }
  .hero-bio { margin: 0 auto 30px; }
  .hero-cta { justify-content: center; }
  .hero-image-block { order: -1; } /* Foto pindah ke atas teks */
  .profile-frame { max-width: 320px; }
}

@media (max-width: 768px) {
  .nav-links { display: none; }
  .hero-name { font-size: 3.5rem; }
  .profile-frame { max-width: 250px; }
  .section-title { font-size: 2.8rem; }
  .footer-inner { flex-direction: column; gap: 15px; text-align: center; }
}
</style>