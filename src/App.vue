<script setup>
import { ref } from 'vue'

const projects = ref([
  {
    title: 'Sistem Digitalisasi CSR',
    desc: 'Aplikasi pengelolaan Corporate Social Responsibility berbasis web.',
    tech: ['Laravel', 'Vue.js', 'MySQL'],
    link: '#' // Ganti dengan link repo atau demo kalau ada
  },
  {
    title: 'DesaGo Market',
    desc: 'Platform marketplace untuk pemberdayaan ekonomi desa.',
    tech: ['Web Development', 'UI/UX'],
    link: '#'
  },
  {
    title: 'Digital Packaging Approval',
    desc: 'Sistem digitalisasi formulir persetujuan kemasan (Paperless Office).',
    tech: ['System Analysis', 'Web App'],
    link: '#'
  },
  {
    title: 'Atribut Paskibra Cikarang (APC)',
    desc: 'Pengembangan sistem manajemen bisnis dan portofolio e-commerce.',
    tech: ['Business Logic', 'Web Dev'],
    link: '#'
  }
])

const contact = {
  email: 'email.kamu@example.com', // GANTI INI
  linkedin: 'https://linkedin.com/in/username-kamu', // GANTI INI
  github: 'https://github.com/username-kamu' // GANTI INI
}
</script>

<template>
  <div class="container">
    <header class="hero">
      <h1>Halo, Saya <span class="highlight">Abid Azis</span> 👋</h1>
      <p class="subtitle">Mahasiswa Sistem Informasi (Semester 7) | Web Developer</p>
      <p class="bio">
        Fokus pada pengembangan aplikasi web dengan <strong>Laravel & Vue.js</strong>. 
        Berpengalaman membangun sistem digitalisasi bisnis dan manajemen proyek.
      </p>
      <div class="cta-buttons">
        <a :href="'mailto:' + contact.email" class="btn primary">Hubungi Saya</a>
        <a :href="contact.github" target="_blank" class="btn secondary">GitHub</a>
      </div>
    </header>

    <section class="projects">
      <h2>Proyek Unggulan</h2>
      <div class="grid">
        <div v-for="(item, index) in projects" :key="index" class="card">
          <h3>{{ item.title }}</h3>
          <p>{{ item.desc }}</p>
          <div class="tags">
            <span v-for="tech in item.tech" :key="tech" class="tag">{{ tech }}</span>
          </div>
          <a v-if="item.link !== '#'" :href="item.link" target="_blank" class="link-text">Lihat Detail →</a>
        </div>
      </div>
    </section>

    <footer>
      <p>© 2026 Abid Azis. Dibuat dengan Vue.js.</p>
    </footer>
  </div>
</template>

<style scoped>
/* Reset & Base */
* { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Inter', sans-serif; }
.container { max-width: 800px; margin: 0 auto; padding: 40px 20px; color: #333; }

/* Hero Section */
.hero { text-align: center; margin-bottom: 60px; }
h1 { font-size: 2.5rem; margin-bottom: 10px; }
.highlight { color: #42b883; /* Vue Green */ }
.subtitle { font-size: 1.2rem; color: #666; margin-bottom: 20px; }
.bio { max-width: 600px; margin: 0 auto 30px; line-height: 1.6; }

/* Buttons */
.cta-buttons { display: flex; gap: 15px; justify-content: center; }
.btn { padding: 10px 20px; border-radius: 6px; text-decoration: none; font-weight: bold; transition: 0.3s; }
.primary { background: #35495e; color: white; }
.primary:hover { background: #42b883; }
.secondary { border: 2px solid #35495e; color: #35495e; }
.secondary:hover { background: #f4f4f4; }

/* Projects Grid */
.projects h2 { border-bottom: 2px solid #eee; padding-bottom: 10px; margin-bottom: 20px; }
.grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 20px; }
.card { border: 1px solid #ddd; padding: 20px; border-radius: 8px; transition: transform 0.2s; background: #fff; }
.card:hover { transform: translateY(-5px); box-shadow: 0 5px 15px rgba(0,0,0,0.1); }
.card h3 { margin-bottom: 10px; color: #2c3e50; }
.card p { font-size: 0.9rem; color: #555; margin-bottom: 15px; line-height: 1.5; }

/* Tags */
.tags { display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 15px; }
.tag { background: #eef; color: #35495e; font-size: 0.8rem; padding: 4px 8px; border-radius: 4px; }
.link-text { color: #42b883; text-decoration: none; font-weight: bold; font-size: 0.9rem; }
.link-text:hover { text-decoration: underline; }

/* Footer */
footer { text-align: center; margin-top: 50px; color: #888; font-size: 0.8rem; }
</style>