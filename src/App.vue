<script setup>
import { ref, onMounted } from 'vue'

// Data Profil
const profile = {
  name: 'Abid Azis',
  role: 'Full-Stack Web Developer',
  tagline: 'Membangun solusi digital yang efisien dan skalabel.',
  bio: 'Mahasiswa Sistem Informasi Universitas Singaperbangsa Karawang (UNSIKA) yang memiliki passion kuat dalam pengembangan aplikasi web. Berpengalaman menggunakan ekosistem Laravel dan Vue.js untuk mendesain sistem digitalisasi bisnis, workflow perusahaan, dan manajemen operasional.'
}

// Data Skills
const skills = ref(['Laravel', 'Vue.js', 'Livewire', 'MySQL', 'System Analysis', 'UI/UX Design', 'Tailwind CSS', 'Git'])

// Data Pengalaman
const experiences = ref([
  {
    role: 'MIS Intern (Management Information System)',
    company: 'PT Kayaba Indonesia',
    period: '2025 - Sekarang',
    desc: 'Mengembangkan sistem workflow persetujuan dokumen kemasan berbasis web untuk efisiensi proses bisnis (Paperless Office).'
  },
  {
    role: 'Founder & Manager',
    company: 'Atribut Paskibra Cikarang (APC) & Anti Polos',
    period: '2022 - Sekarang',
    desc: 'Mengelola operasional bisnis, produksi atribut, sablon, serta mengembangkan sistem manajemen pemesanan secara mandiri.'
  },
  {
    role: 'Paskibra Coach / Ganapatra Management',
    company: 'Berbagai Sekolah di Cikarang',
    period: 'Aktif',
    desc: 'Melatih kepemimpinan, kedisiplinan, dan manajemen acara komunitas kepemudaan.'
  }
])

// Data Proyek (Disesuaikan dengan real project)
const projects = ref([
  {
    title: 'Packaging Document Approval Workflow',
    desc: 'Sistem digitalisasi formulir persetujuan kemasan untuk efisiensi bisnis (Studi Kasus: PT. Kayaba Indonesia).',
    tech: ['Laravel', 'Vue.js', 'System Analysis'],
    link: '#',
    github: '#'
  },
  {
    title: 'PANDARA Scoring System',
    desc: 'Sistem informasi penilaian lomba Paskibra secara real-time dan akurat terintegrasi database.',
    tech: ['Laravel', 'Livewire', 'MySQL'],
    link: '#',
    github: '#'
  },
  {
    title: 'E-Report Card System',
    desc: 'Sistem manajemen e-rapor terintegrasi untuk memudahkan guru dalam mengolah dan menerbitkan nilai siswa.',
    tech: ['Web Development', 'Database Management'],
    link: '#',
    github: '#'
  },
  {
    title: 'APC Business Management',
    desc: 'Aplikasi internal untuk manajemen stok, kasir, dan portofolio e-commerce Atribut Paskibra Cikarang.',
    tech: ['Vue.js', 'Business Logic'],
    link: '#',
    github: '#'
  }
])

const contact = {
  email: 'abidazis@example.com', // Sesuaikan
  linkedin: 'https://linkedin.com/in/username-kamu', // Sesuaikan
  github: 'https://github.com/username-kamu', // Sesuaikan
  instagram: 'https://instagram.com/username-kamu' // Sesuaikan
}

// Simple scroll animation logic
onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('show')
      }
    })
  })
  
  document.querySelectorAll('.animate-on-scroll').forEach((el) => {
    observer.observe(el)
  })
})
</script>

<template>
  <div class="app-wrapper">
    <nav class="navbar">
      <div class="nav-content">
        <span class="logo">Abid<span class="highlight">.dev</span></span>
        <div class="nav-links">
          <a href="#about">Tentang</a>
          <a href="#experience">Pengalaman</a>
          <a href="#projects">Proyek</a>
          <a href="#contact" class="nav-cta">Kontak</a>
        </div>
      </div>
    </nav>

    <main class="container">
      <section id="hero" class="hero animate-on-scroll">
        <div class="hero-text">
          <p class="greeting">Halo, Saya</p>
          <h1 class="gradient-text">{{ profile.name }}</h1>
          <h2 class="subtitle">{{ profile.role }}</h2>
          <p class="bio">{{ profile.bio }}</p>
          
          <div class="skills-wrapper">
            <span v-for="skill in skills" :key="skill" class="skill-pill">{{ skill }}</span>
          </div>

          <div class="cta-buttons">
            <a :href="'mailto:' + contact.email" class="btn primary">
              Mulai Diskusi
            </a>
            <a :href="contact.github" target="_blank" class="btn secondary">
              Lihat GitHub
            </a>
          </div>
        </div>
      </section>

      <section id="experience" class="experience section-pad animate-on-scroll">
        <h2 class="section-title">Perjalanan Karir & Bisnis</h2>
        <div class="timeline">
          <div v-for="(exp, index) in experiences" :key="index" class="timeline-item">
            <div class="timeline-dot"></div>
            <div class="timeline-content card-glass">
              <h3>{{ exp.role }}</h3>
              <span class="company">{{ exp.company }} | {{ exp.period }}</span>
              <p>{{ exp.desc }}</p>
            </div>
          </div>
        </div>
      </section>

      <section id="projects" class="projects section-pad animate-on-scroll">
        <h2 class="section-title">Proyek & Karya</h2>
        <div class="grid">
          <div v-for="(item, index) in projects" :key="index" class="card card-glass group">
            <div class="card-header">
              <svg class="folder-icon" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 19a2 2 0 0 1-2 2H4a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h5l2 3h9a2 2 0 0 1 2 2z"></path></svg>
              <div class="card-links">
                <a :href="item.github" target="_blank" title="GitHub Repo">
                  <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"></path></svg>
                </a>
                <a :href="item.link" target="_blank" title="Live Demo">
                  <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"></path><polyline points="15 3 21 3 21 9"></polyline><line x1="10" y1="14" x2="21" y2="3"></line></svg>
                </a>
              </div>
            </div>
            <h3>{{ item.title }}</h3>
            <p>{{ item.desc }}</p>
            <div class="tags">
              <span v-for="tech in item.tech" :key="tech" class="tag">{{ tech }}</span>
            </div>
          </div>
        </div>
      </section>
    </main>

    <footer id="contact" class="footer">
      <div class="footer-content animate-on-scroll">
        <h2>Tertarik untuk berkolaborasi?</h2>
        <p>Mari diskusikan ide, proyek web, atau peluang kerja sama.</p>
        <a :href="'mailto:' + contact.email" class="btn primary footer-btn">Say Hello</a>
        <div class="social-links">
          <a :href="contact.linkedin" target="_blank">LinkedIn</a>
          <a :href="contact.github" target="_blank">GitHub</a>
          <a :href="contact.instagram" target="_blank">Instagram</a>
        </div>
        <p class="copyright">© 2026 Abid Azis. Dibuat dengan Vue.js & Vite.</p>
      </div>
    </footer>
  </div>
</template>

<style scoped>
/* ================= VARIABLES ================= */
:root {
  --bg-dark: #0f172a;
  --bg-surface: #1e293b;
  --bg-surface-hover: #334155;
  --text-main: #f8fafc;
  --text-muted: #94a3b8;
  --accent: #10b981; /* Emerald / Vue Green */
  --accent-glow: rgba(16, 185, 129, 0.4);
}

/* ================= RESET & BASE ================= */
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  scroll-behavior: smooth;
}

.app-wrapper {
  background-color: var(--bg-dark);
  color: var(--text-main);
  min-height: 100vh;
  overflow-x: hidden;
  line-height: 1.6;
}

.container {
  max-width: 1000px;
  margin: 0 auto;
  padding: 0 24px;
}

.section-pad {
  padding: 100px 0;
}

.highlight { color: var(--accent); }

/* ================= TYPOGRAPHY ================= */
.gradient-text {
  font-size: clamp(3rem, 8vw, 5rem);
  font-weight: 800;
  background: linear-gradient(135deg, #34d399, #059669);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  margin-bottom: 10px;
  line-height: 1.1;
}

.section-title {
  font-size: 2rem;
  margin-bottom: 40px;
  display: flex;
  align-items: center;
  gap: 15px;
}

.section-title::after {
  content: "";
  height: 1px;
  flex-grow: 1;
  background-color: var(--bg-surface-hover);
}

/* ================= NAVBAR ================= */
.navbar {
  position: fixed;
  top: 0;
  width: 100%;
  backdrop-filter: blur(10px);
  background: rgba(15, 23, 42, 0.8);
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
  z-index: 100;
}

.nav-content {
  max-width: 1000px;
  margin: 0 auto;
  padding: 20px 24px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  font-weight: 700;
  font-size: 1.2rem;
  letter-spacing: -0.5px;
}

.nav-links {
  display: flex;
  gap: 25px;
  align-items: center;
}

.nav-links a {
  color: var(--text-main);
  text-decoration: none;
  font-size: 0.9rem;
  font-weight: 500;
  transition: color 0.3s;
}

.nav-links a:hover {
  color: var(--accent);
}

.nav-cta {
  border: 1px solid var(--accent);
  padding: 6px 16px;
  border-radius: 4px;
  color: var(--accent) !important;
}
.nav-cta:hover {
  background: rgba(16, 185, 129, 0.1);
}

/* ================= HERO ================= */
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  padding-top: 80px;
}

.hero-text {
  max-width: 700px;
}

.greeting {
  color: var(--accent);
  font-family: monospace;
  font-size: 1.1rem;
  margin-bottom: 10px;
}

.subtitle {
  font-size: clamp(1.5rem, 4vw, 2.5rem);
  color: var(--text-muted);
  margin-bottom: 24px;
}

.bio {
  font-size: 1.1rem;
  color: var(--text-muted);
  margin-bottom: 30px;
  max-width: 600px;
}

.skills-wrapper {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-bottom: 40px;
}

.skill-pill {
  background: var(--bg-surface);
  color: var(--accent);
  padding: 6px 14px;
  border-radius: 20px;
  font-size: 0.85rem;
  font-weight: 500;
  border: 1px solid rgba(16, 185, 129, 0.2);
}

/* ================= BUTTONS ================= */
.cta-buttons { display: flex; gap: 15px; }
.btn {
  padding: 14px 28px;
  border-radius: 6px;
  text-decoration: none;
  font-weight: 600;
  transition: all 0.3s ease;
  display: inline-block;
}
.primary {
  background: var(--accent);
  color: var(--bg-dark);
}
.primary:hover {
  background: #059669;
  box-shadow: 0 0 15px var(--accent-glow);
  transform: translateY(-2px);
}
.secondary {
  border: 1px solid var(--text-muted);
  color: var(--text-main);
}
.secondary:hover {
  border-color: var(--accent);
  background: rgba(16, 185, 129, 0.05);
  transform: translateY(-2px);
}

/* ================= TIMELINE (EXPERIENCE) ================= */
.timeline {
  position: relative;
  padding-left: 30px;
}
.timeline::before {
  content: '';
  position: absolute;
  left: 0;
  top: 0;
  bottom: 0;
  width: 2px;
  background: var(--bg-surface-hover);
}
.timeline-item {
  position: relative;
  margin-bottom: 40px;
}
.timeline-dot {
  position: absolute;
  left: -35px;
  top: 6px;
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: var(--accent);
  box-shadow: 0 0 10px var(--accent-glow);
}
.company {
  display: block;
  font-family: monospace;
  color: var(--accent);
  margin-bottom: 10px;
  font-size: 0.9rem;
}

/* ================= CARDS (PROJECTS) ================= */
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 24px;
}

.card-glass {
  background: var(--bg-surface);
  border: 1px solid rgba(255, 255, 255, 0.05);
  border-radius: 12px;
  padding: 30px;
  transition: all 0.3s ease;
}

.card-glass:hover {
  transform: translateY(-8px);
  border-color: rgba(16, 185, 129, 0.3);
  box-shadow: 0 10px 30px -15px rgba(2, 12, 27, 0.7);
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 25px;
}

.folder-icon { color: var(--accent); width: 40px; height: 40px; }
.card-links { display: flex; gap: 15px; }
.card-links a { color: var(--text-muted); transition: color 0.3s; }
.card-links a:hover { color: var(--accent); }

.card-glass h3 { font-size: 1.4rem; margin-bottom: 10px; color: var(--text-main); }
.card-glass p { color: var(--text-muted); font-size: 0.95rem; margin-bottom: 20px; }

.tags { display: flex; flex-wrap: wrap; gap: 10px; margin-top: auto; }
.tag { font-family: monospace; font-size: 0.8rem; color: var(--text-muted); }

/* ================= FOOTER ================= */
.footer {
  text-align: center;
  padding: 100px 20px 50px;
}
.footer-content h2 { margin-bottom: 15px; }
.footer-content p { color: var(--text-muted); margin-bottom: 30px; }
.footer-btn { margin-bottom: 50px; }
.social-links { display: flex; justify-content: center; gap: 20px; margin-bottom: 30px; }
.social-links a { color: var(--text-main); text-decoration: none; font-size: 0.9rem; transition: 0.3s; }
.social-links a:hover { color: var(--accent); }
.copyright { font-size: 0.8rem !important; color: #64748b !important; }

/* ================= ANIMATIONS ================= */
.animate-on-scroll {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.8s ease-out, transform 0.8s ease-out;
}
.animate-on-scroll.show {
  opacity: 1;
  transform: translateY(0);
}

/* ================= RESPONSIVE ================= */
@media (max-width: 768px) {
  .nav-links { display: none; /* Simplifikasi mobile view */ }
  .gradient-text { font-size: 2.5rem; }
  .section-pad { padding: 60px 0; }
  .cta-buttons { flex-direction: column; width: 100%; }
  .btn { text-align: center; }
}
</style>