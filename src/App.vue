<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'
import './assets/style.css'

// --- 1. IMPORT ASSETS ---
import profileImg from './assets/images/profile.jpg'
import heroBg from './assets/images/hero-bg.webp'

import p1_1 from './assets/images/projects/p1-1.jpg'
import p1_2 from './assets/images/projects/p1-2.png'
import p1_3 from './assets/images/projects/p1-3.png'
import p1_4 from './assets/images/projects/p1-4.png'

import p2_1 from './assets/images/projects/p2-1.jpg'
import p2_2 from './assets/images/projects/p2-2.png'
import p2_3 from './assets/images/projects/p2-3.png'

import p3_1 from './assets/images/projects/p3-1.jpg'
import p3_2 from './assets/images/projects/p3-2.png'
import p3_3 from './assets/images/projects/p3-3.png'

import p4_1 from './assets/images/projects/p4-1.jpg'
import p4_2 from './assets/images/projects/p4-2.png'
import p4_3 from './assets/images/projects/p4-3.jpg'

import p5_1 from './assets/images/projects/p5-1.png'
import p5_2 from './assets/images/projects/p5-2.png'
import p5_3 from './assets/images/projects/p5-3.png'

// --- 2. BILINGUAL LANGUAGE LOGIC (NEW) ---
const lang = ref('id') // Default bahasa: Indonesia

const toggleLanguage = () => {
  lang.value = lang.value === 'id' ? 'en' : 'id'
}

// Dictionary untuk teks statis
const dict = {
  id: {
    nav: { services: 'Layanan', skills: 'Keahlian', journey: 'Perjalanan', work: 'Projek', hire: 'Rekrut Saya' },
    hero: { greeting: 'Hai, saya', titleBase: 'Fullstack Web Developer', titleHighlight: 'Membangun Web Skalabel', bio: 'Saya membantu bisnis bertransformasi dan berkembang lewat sistem informasi web yang cepat, modern, dan andal. Berbekal keahlian profesional di ekosistem Laravel & Vue.js, fokus saya adalah mengubah alur kerja konvensional menjadi aplikasi manajemen berbasis digital yang efisien dan tepat sasaran.', cv: 'Unduh CV', work: 'Lihat Projek' },
    services: { tag: 'Yang Saya Tawarkan', title: 'Layanan Profesional' },
    skills: { tag: 'Andalan Saya', title: 'Teknologi & Alat' },
    experience: { tag: 'Perjalanan Saya', title: 'Pengalaman & Pendidikan', emptyExp: 'Belum ada pengalaman.', emptyEdu: 'Belum ada riwayat pendidikan.' },
    projects: { tag: 'Portofolio Unggulan', title: 'Projek Pilihan', empty: 'Belum ada proyek yang ditambahkan.' },
    cta: { title: 'Mari Bangun Sesuatu yang Luar Biasa.', desc: 'Saya saat ini terbuka untuk peluang kerja full-time, proyek lepas (freelance), maupun kolaborasi pengembangan perangkat lunak tingkat korporat. Mari bicarakan bagaimana kapabilitas saya dapat memberikan solusi nyata bagi tim Anda.', btnEmail: 'Kirim Email', btnLinkedIn: 'Terhubung di LinkedIn' },
    footer: { text: 'Dibuat dengan' },
    modal: { impact: 'Dampak / Metrik Utama', desc: 'Deskripsi Projek', contrib: 'Kontribusi & Implementasi Teknis', demo: 'Lihat Langsung ↗', source: 'Kode Sumber' }
  },
  en: {
    nav: { services: 'Services', skills: 'Skills', journey: 'Journey', work: 'Work', hire: 'Hire Me' },
    hero: { greeting: "Hi, I'm", titleBase: 'Fullstack Web Developer', titleHighlight: 'Building Scalable Web', bio: 'I help businesses transform and grow through fast, modern, and reliable web information systems. Armed with professional expertise in the Laravel & Vue.js ecosystem, my focus is converting conventional workflows into highly efficient and targeted digital management applications.', cv: 'Download CV', work: 'View Work' },
    services: { tag: 'What I Offer', title: 'Professional Services' },
    skills: { tag: 'My Arsenal', title: 'Tech Stack & Tools' },
    experience: { tag: 'My Journey', title: 'Experience & Education', emptyExp: 'No experience yet.', emptyEdu: 'No education history yet.' },
    projects: { tag: 'Featured Portfolio', title: 'Selected Works', empty: 'No projects added yet.' },
    cta: { title: "Let's Build Something Amazing Together.", desc: "I am currently open for full-time opportunities, freelance projects, or corporate software development collaborations. Let's discuss how my capabilities can provide real solutions for your team.", btnEmail: 'Send an Email', btnLinkedIn: 'Connect on LinkedIn' },
    footer: { text: 'Crafted with' },
    modal: { impact: 'Key Impact / Metric', desc: 'Project Description', contrib: 'Contributions & Technical Implementation', demo: 'Live Demo ↗', source: 'Source Code' }
  }
}

const t = computed(() => dict[lang.value])

// --- 3. MOBILE NAVIGATION LOGIC ---
const isMobileMenuOpen = ref(false)
const toggleMobileMenu = () => { isMobileMenuOpen.value = !isMobileMenuOpen.value }
const closeMobileMenu = () => { isMobileMenuOpen.value = false }

const handleResize = () => { if (window.innerWidth >= 768) closeMobileMenu() }
onMounted(() => { window.addEventListener('resize', handleResize) })
onUnmounted(() => { window.removeEventListener('resize', handleResize) })

// --- 4. DYNAMIC DATA (REACTIVE TO LANGUAGE) ---
const services = computed(() => lang.value === 'id' ? [
  { icon: 'fas fa-server', title: 'Pengembangan API Backend', desc: 'Membangun arsitektur server yang kokoh, scalable, dan aman menggunakan Laravel. Ahli dalam merancang RESTful API dan optimasi query database.' },
  { icon: 'fas fa-laptop-code', title: 'Integrasi Frontend', desc: 'Transformasi desain UI/UX menjadi interface interaktif, cepat, dan responsif menggunakan Vue.js dan Tailwind CSS dengan state-management.' },
  { icon: 'fas fa-cogs', title: 'Solusi MIS Perusahaan', desc: 'Spesialisasi dalam mendigitalisasi alur kerja konvensional perusahaan menjadi Sistem Informasi Manajemen (MIS) berbasis web untuk efisiensi bisnis.' }
] : [
  { icon: 'fas fa-server', title: 'Backend API Development', desc: 'Building robust, scalable, and secure server architecture using Laravel. Expert in designing RESTful APIs and database query optimization.' },
  { icon: 'fas fa-laptop-code', title: 'Frontend Integration', desc: 'Transforming UI/UX designs into interactive, fast, and responsive interfaces using Vue.js and Tailwind CSS with state-management.' },
  { icon: 'fas fa-cogs', title: 'Enterprise MIS Solution', desc: 'Specializing in digitizing conventional corporate workflows into web-based Management Information Systems (MIS) for business efficiency.' }
])

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

const projects = computed(() => lang.value === 'id' ? [
  {
    id: 1, title: 'Document Approval Workflow',
    shortDesc: 'Sistem alur kerja tanpa kertas (paperless) digital untuk persetujuan dokumen packaging perusahaan.',
    fullDesc: 'Sistem manajemen alur kerja berbasis web komprehensif yang dibangun untuk meningkatkan efisiensi proses bisnis (Paperless Office) pada PT Kayaba Indonesia. Sistem ini mendigitalisasi proses persetujuan dokumen packaging konvensional yang sebelumnya manual.',
    metric: 'Meningkatkan efisiensi waktu approval dokumen spesifikasi hingga 60%',
    contributions: [ 'Merancang arsitektur database relasional untuk menyimpan alur approval multi-level role.', 'Mengembangkan RESTful API menggunakan Laravel untuk mengolah transisi status dokumen.', 'Membangun modul pencatatan riwayat revisi (Revision History) yang dipicu langsung dari aksi modifikasi user/supplier.', 'Mengintegrasikan frontend Vue.js dengan Inertia untuk transisi halaman cepat.' ],
    tech: ['Laravel', 'Vue.js', 'MySQL', 'System Analysis', 'Inertia.js'], link: '#', github: '#', images: [p2_1, p2_2, p2_3]
  },
  {
    id: 2, title: 'Business Travel Management',
    shortDesc: 'Sistem internal perusahaan untuk mengelola pengajuan dan dokumen perjalanan dinas.',
    fullDesc: 'Aplikasi web internal yang dirancang untuk merampingkan manajemen perjalanan dinas perusahaan. Sistem ini memfasilitasi karyawan dalam mengajukan permohonan perjalanan, menangani hirarki persetujuan manajerial, kalkulasi dana tunjangan otomatis, serta penerbitan Surat Perintah Perjalanan Dinas (SPPD) otomatis.',
    metric: 'Mengotomatisasi 100% kalkulasi allowance perjalanan dinas dan pembuatan berkas SPPD',
    contributions: [ 'Membuat kalkulator logika otomatis untuk perhitungan tunjangan dana berdasarkan level jabatan dan destinasi.', 'Membangun sistem approval bertingkat dinamis (Karyawan -> Supervisor -> Dept Head).', 'Mengembangkan fitur auto-generate file PDF formal untuk SPPD.' ],
    tech: ['Laravel', 'Web Development', 'MySQL', 'DomPDF Integration'], link: '#', github: '#', images: [p3_1, p3_2, p3_3]
  },
  {
    id: 3, title: 'Corporate Social Responsibility (CSR) System',
    shortDesc: 'Platform digital untuk mengelola, melacak, dan melaporkan program CSR perusahaan.',
    fullDesc: 'Platform digital terpusat yang diciptakan untuk memantau dan mengelola inisiatif CSR perusahaan secara transparan. Dilengkapi dengan grafik pelacakan anggaran, dokumentasi program di lapangan, manajemen data penerima manfaat, serta generator laporan komprehensif.',
    metric: 'Menyediakan pelacakan budget alokasi dana CSR secara real-time dengan visualisasi grafik',
    contributions: [ 'Mengintegrasikan visualisasi chart interaktif pada dashboard menggunakan Chart.js.', 'Membangun modul pelaporan keuangan CSR yang terbagi per jenis kategori kegiatan.', 'Mengoptimasi performa query rekapitulasi data penerima bantuan sosial.' ],
    tech: ['Laravel', 'Vue.js', 'UI/UX Design', 'Chart.js'], link: '#', github: '#', images: [p1_1, p1_2, p1_3, p1_4]
  },
  {
    id: 4, title: 'DesaGo Market E-Commerce',
    shortDesc: 'Marketplace digital inovatif yang dibangun untuk memberdayakan ekonomi desa.',
    fullDesc: 'DesaGo Market adalah platform e-commerce yang didedikasikan bagi para pelaku usaha dan UMKM di tingkat desa. Menyediakan etalase toko digital modern lengkap dengan keranjang belanja, manajemen stok produk, dan pelacakan pesanan.',
    metric: 'Berhasil di-deploy dan mengelola pemeliharaan berkas sistem pada domain aktif desagomarket.store',
    contributions: [ 'Merancang dan mengimplementasikan sistem manajemen inventori multi-merchant.', 'Membangun keranjang belanja (shopping cart) yang aman dengan manajemen session.', 'Mengelola deployment aplikasi dan pemeliharaan file server secara berkala.' ],
    tech: ['Fullstack PHP', 'E-Commerce Logic', 'UI/UX Framework', 'Deployment Management'], link: '#', github: '#', images: [p4_1, p4_2, p4_3]
  },
  {
    id: 5, title: 'PANDARA Scoring System',
    shortDesc: 'Sistem penilaian dan papan skor real-time untuk kompetisi Paskibra.',
    fullDesc: 'PANDARA adalah sistem manajemen penilaian khusus yang dirancang untuk perlombaan Paskibra Formasi dan Baris-Berbaris. Sistem ini meminimalisir kesalahan manusia dengan menyediakan antarmuka digital bagi juri untuk menginput nilai secara langsung.',
    metric: 'Mempercepat kalkulasi skor akhir kompetisi dari hitungan jam menjadi hitungan detik secara otomatis',
    contributions: [ 'Membangun arsitektur algoritma perhitungan bobot nilai juri yang rumit secara real-time.', 'Menggunakan teknologi reaktif untuk pembaruan papan skor (leaderboard) penonton.', 'Membuat sistem validasi input juri untuk mencegah anomali skor.' ],
    tech: ['Laravel', 'Livewire', 'Database Architecture', 'Algoritma Penilaian'], link: '#', github: '#', images: [p5_1, p5_2, p5_3] 
  }
] : [
  {
    id: 1, title: 'Document Approval Workflow',
    shortDesc: 'A digital paperless workflow system for enterprise packaging document approvals.',
    fullDesc: 'A comprehensive web-based workflow management system built to improve business process efficiency (Paperless Office) at PT Kayaba Indonesia. This system digitizes the manual packaging document approval process.',
    metric: 'Increased specification document approval time efficiency by up to 60%',
    contributions: [ 'Designed relational database architecture to store multi-level role approval workflows.', 'Developed RESTful APIs using Laravel to process document status transitions.', 'Built a Revision History module triggered directly by user/supplier modification actions.', 'Integrated Vue.js frontend with Inertia for fast page transitions.' ],
    tech: ['Laravel', 'Vue.js', 'MySQL', 'System Analysis', 'Inertia.js'], link: '#', github: '#', images: [p2_1, p2_2, p2_3]
  },
  {
    id: 2, title: 'Business Travel Management',
    shortDesc: 'Internal corporate system for managing business travel requests and documentation.',
    fullDesc: 'An internal web application designed to streamline corporate business travel management. The system facilitates employees in submitting travel requests, handling managerial approval hierarchies, automatic allowance calculation, and generating SPPD documents.',
    metric: 'Automated 100% of business travel allowance calculations and SPPD document generation.',
    contributions: [ 'Created an automatic logic calculator for allowance calculation based on job level and destination.', 'Built a dynamic multi-level approval system (Employee -> Supervisor -> Dept Head).', 'Developed an auto-generate formal PDF feature for SPPD.' ],
    tech: ['Laravel', 'Web Development', 'MySQL', 'DomPDF Integration'], link: '#', github: '#', images: [p3_1, p3_2, p3_3]
  },
  {
    id: 3, title: 'Corporate Social Responsibility (CSR) System',
    shortDesc: 'Digital platform to manage, track, and report corporate CSR programs.',
    fullDesc: 'A centralized digital platform created to monitor and manage corporate CSR initiatives transparently. Equipped with budget tracking charts, field program documentation, beneficiary data management, and a comprehensive report generator.',
    metric: 'Provided real-time CSR fund allocation budget tracking with interactive chart visualization.',
    contributions: [ 'Integrated interactive chart visualization on the dashboard using Chart.js.', 'Built a CSR financial reporting module divided by activity category type.', 'Optimized query performance for social assistance recipient data recapitulation.' ],
    tech: ['Laravel', 'Vue.js', 'UI/UX Design', 'Chart.js'], link: '#', github: '#', images: [p1_1, p1_2, p1_3, p1_4]
  },
  {
    id: 4, title: 'DesaGo Market E-Commerce',
    shortDesc: 'An innovative digital marketplace built to empower the village economy.',
    fullDesc: 'DesaGo Market is an e-commerce platform dedicated to local village entrepreneurs and MSMEs. It provides a modern digital storefront complete with a shopping cart, product stock management, and order tracking.',
    metric: 'Successfully deployed and maintained system files on the active domain desagomarket.store.',
    contributions: [ 'Designed and implemented a multi-merchant inventory management system.', 'Built a secure shopping cart with session management.', 'Managed application deployment and periodic server file maintenance.' ],
    tech: ['Fullstack PHP', 'E-Commerce Logic', 'UI/UX Framework', 'Deployment Management'], link: '#', github: '#', images: [p4_1, p4_2, p4_3]
  },
  {
    id: 5, title: 'PANDARA Scoring System',
    shortDesc: 'Real-time scoring and leaderboard system for Paskibra competitions.',
    fullDesc: 'PANDARA is a specialized scoring management system designed for Paskibra Formation competitions. This system minimizes human error by providing a digital interface for judges to input scores directly.',
    metric: 'Accelerated the calculation of final competition scores from hours to seconds automatically.',
    contributions: [ 'Built a complex real-time judge scoring weight calculation algorithm architecture.', 'Used reactive technology for audience leaderboard updates.', 'Created a judge input validation system to prevent score range anomalies.' ],
    tech: ['Laravel', 'Livewire', 'Database Architecture', 'Algoritma Penilaian'], link: '#', github: '#', images: [p5_1, p5_2, p5_3] 
  }
])

const experiences = computed(() => lang.value === 'id' ? [
  { id: 1, type: 'education', role: 'Pendidikan Menengah Kejuruan (Teknik Komputer & Jaringan)', company: 'SMKN 1 Cikarang Selatan', period: '2019 - 2022', desc: 'Lulus dengan nilai rata-rata akhir memuaskan sebesar 82.50 dengan pemahaman dasar jaringan dan perangkat keras komputer.' },
  { id: 2, type: 'education', role: 'Sarjana Komputer (S.Kom.) - Sistem Informasi', company: 'Universitas Singaperbangsa Karawang (UNSIKA)', period: '2022 - 2026', desc: 'Lulus dengan predikat kehormatan tertinggi (Summa Cum Laude) dengan IPK 3.93. Berfokus pada digitalisasi sistem informasi korporat. Berhasil mempertahankan skripsi mengenai rancang bangun sistem workflow persetujuan dokumen packaging berbasis web.' },
  { id: 3, type: 'education', role: 'Sertifikasi Junior Web Developer', company: 'BPPTIK - KOMINFO', period: '2023', desc: 'Menyelesaikan proyek pembuatan aplikasi web mandiri dengan hasil memuaskan dan dinyatakan lulus uji kompetensi standar BNSP untuk Junior Web Development.' },
  { id: 4, type: 'education', role: 'Studi Independen Bersertifikat (Full-Stack Developer)', company: 'Rakamin Academy x Kemendikbudristek (Program MSIB)', period: '2023', desc: 'Mengikuti program intensif "IT Full Stack Developer: Mastering Web Development Blending With Data Science" dengan penguasaan kurikulum backend, frontend, hingga fondasi pengolahan data sistem.' },
  { id: 5, type: 'work', role: 'Freelance Full-Stack Developer', company: 'Self-Employed / Berbagai Klien', period: '2025 - Sekarang', desc: 'Mengembangkan aplikasi kustom berbasis web untuk klien lokal. Proyek terbaru mencakup Sistem Rekap Penilaian Lomba Paskibra, website profile perusahaan pakaian Quenna, serta sistem administrasi inventori UMKM.' },
  { id: 6, type: 'work', role: 'MIS (Management Information System) Intern', company: 'PT Kayaba Indonesia', period: 'Agu 2025 - Jan 2026', desc: 'Bertindak sebagai Fullstack Web Developer magang di bawah supervisi departemen MIS. Bertanggung jawab penuh merancang, membangun, dan menguji 3 sistem internal perusahaan (CSR Tracking, Packaging Standards, dan Business Travel Authorization).' },
] : [
  { id: 1, type: 'education', role: 'Vocational High School (Computer & Network Engineering)', company: 'SMKN 1 Cikarang Selatan', period: '2019 - 2022', desc: 'Graduated with a satisfactory final average score of 82.50 with a basic understanding of networking and computer hardware.' },
  { id: 2, type: 'education', role: 'Bachelor of Computer Science - Information Systems', company: 'Universitas Singaperbangsa Karawang (UNSIKA)', period: '2022 - 2026', desc: 'Graduated with highest honors (Summa Cum Laude) with a 3.93 GPA. Focused on corporate information system digitization. Successfully defended a thesis on the design of a web-based packaging document approval workflow system.' },
  { id: 3, type: 'education', role: 'Certified Junior Web Developer', company: 'BPPTIK - KOMINFO', period: '2023', desc: 'Completed an independent web application project with satisfactory results and passed the BNSP standard competency test for Junior Web Development.' },
  { id: 4, type: 'education', role: 'Certified Independent Study (Full-Stack Developer)', company: 'Rakamin Academy x Kemendikbudristek', period: '2023', desc: 'Participated in the intensive "IT Full Stack Developer: Mastering Web Development Blending With Data Science" program, mastering backend, frontend, and data processing foundations.' },
  { id: 5, type: 'work', role: 'Freelance Full-Stack Developer', company: 'Self-Employed / Various Clients', period: '2025 - Present', desc: 'Developing custom web-based applications for local clients. Recent projects include the Paskibra Competition Scoring Recap System, Quenna clothing company profile website, and MSME inventory administration system.' },
  { id: 6, type: 'work', role: 'MIS (Management Information System) Intern', company: 'PT Kayaba Indonesia', period: 'Aug 2025 - Jan 2026', desc: 'Acted as a Fullstack Web Developer intern under the supervision of the MIS department. Fully responsible for designing, building, and testing 3 internal corporate systems (CSR Tracking, Packaging Standards, and Business Travel Authorization).' },
])

const contact = {
  email: 'abidathanandaazis@gmail.com',
  linkedin: 'https://www.linkedin.com/in/abid-athananda-azis/',
  github: 'https://github.com/abidazis',
  cvFile: '/CV_Abid_Azis.pdf'
}

// --- 5. MODAL LOGIC (POP-UP) ---
const isModalOpen = ref(false)
const selectedProject = ref(null)

const openModal = (project) => {
  selectedProject.value = project; isModalOpen.value = true; document.body.style.overflow = 'hidden' 
}
const closeModal = () => {
  isModalOpen.value = false; setTimeout(() => { selectedProject.value = null }, 300); document.body.style.overflow = 'auto' 
}
</script>

<template>
  <div class="app-wrapper">
    <div class="global-overlay"></div>

    <nav class="navbar">
      <div class="nav-container">
        <span class="logo">Abid<span class="highlight">.</span> Athananda Azis</span>
        
        <div class="nav-links desktop-only">
          <a href="#services">{{ t.nav.services }}</a>
          <a href="#skills">{{ t.nav.skills }}</a>
          <a href="#experience">{{ t.nav.journey }}</a>
          <a href="#projects">{{ t.nav.work }}</a>
          <a :href="contact.github" target="_blank">Git</a>
          
          <button @click="toggleLanguage" class="lang-toggle" :title="lang === 'id' ? 'Switch to English' : 'Ganti ke Bahasa Indonesia'">
            <i class="fas fa-globe"></i> {{ lang === 'id' ? 'ID' : 'EN' }}
          </button>
          
          <a href="#cta" class="nav-cta">{{ t.nav.hire }}</a>
        </div>

        <div style="display: flex; gap: 15px; align-items: center;" class="md-hidden">
          <button @click="toggleLanguage" class="lang-toggle mobile-lang-btn">
            {{ lang === 'id' ? 'ID' : 'EN' }}
          </button>
          
          <button class="hamburger-menu" @click="toggleMobileMenu" aria-label="Toggle Menu">
            <div class="bar" :class="{ 'rotate-top': isMobileMenuOpen }"></div>
            <div class="bar" :class="{ 'fade-out': isMobileMenuOpen }"></div>
            <div class="bar" :class="{ 'rotate-bottom': isMobileMenuOpen }"></div>
          </button>
        </div>
      </div>

      <Transition name="slide-down">
        <div v-if="isMobileMenuOpen" class="mobile-nav-dropdown">
          <a href="#services" @click="closeMobileMenu">{{ t.nav.services }}</a>
          <a href="#skills" @click="closeMobileMenu">{{ t.nav.skills }}</a>
          <a href="#experience" @click="closeMobileMenu">{{ t.nav.journey }}</a>
          <a href="#projects" @click="closeMobileMenu">{{ t.nav.work }}</a>
          <a :href="contact.github" target="_blank" @click="closeMobileMenu">Git</a>
          <a href="#cta" class="mobile-nav-cta" @click="closeMobileMenu">{{ t.nav.hire }}</a>
        </div>
      </Transition>
    </nav>

    <main class="main-content">
      <section class="hero" :style="{ backgroundImage: `url(${heroBg})` }">
        <div class="hero-overlay"></div>
        <div class="container hero-inner">
          <div class="hero-text-block">
            <p class="greeting">{{ t.hero.greeting }} <span class="hand-icon">👋</span></p>
            <h1 class="hero-name gradient-text">Abid Azis</h1>
            <h2 class="hero-title">{{ t.hero.titleBase }} | <span class="highlight">{{ t.hero.titleHighlight }}</span></h2>
            <p class="hero-bio">{{ t.hero.bio }}</p>

            <div class="hero-cta">
              <a :href="contact.cvFile" download target="_blank" class="btn btn-primary">
                <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path><polyline points="7 10 12 15 17 10"></polyline><line x1="12" y1="15" x2="12" y2="3"></line></svg>
                {{ t.hero.cv }}
              </a>
              <a href="#projects" class="btn btn-secondary">{{ t.hero.work }}</a>
            </div>
          </div>
          
          <div class="hero-image-block">
            <div class="profile-frame">
              <img :src="profileImg" alt="Abid Azis" class="profile-photo" />
            </div>
          </div>
        </div>
      </section>

      <section id="services" class="services-section container" style="padding: 80px 0 30px;">
        <div class="section-header text-center">
          <p class="section-tag">{{ t.services.tag }}</p>
          <h2 class="section-title">{{ t.services.title }}</h2>
          <div class="title-line mx-auto"></div>
        </div>
        <div class="project-grid" style="margin-top: 40px;">
          <div v-for="service in services" :key="service.title" class="timeline-content" style="transform: none; hover: translateY(-4px)">
            <div style="display: flex; align-items: center; gap: 15px; margin-bottom: 15px;">
              <i :class="service.icon" class="text-3xl" style="color: var(--accent)"></i>
              <h3 class="text-xl font-bold" style="color: #fff">{{ service.title }}</h3>
            </div>
            <p style="color: #94a3b8; font-size: 0.95rem; line-height: 1.6;">{{ service.desc }}</p>
          </div>
        </div>
      </section>

      <section id="skills" class="skills-section">
        <div class="container">
          <div class="section-header text-center">
            <p class="section-tag">{{ t.skills.tag }}</p>
            <h2 class="section-title">{{ t.skills.title }}</h2>
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

      <section id="experience" class="experience-section">
        <div class="container">
          <div class="section-header text-center">
            <p class="section-tag">{{ t.experience.tag }}</p>
            <h2 class="section-title">{{ t.experience.title }}</h2>
            <div class="title-line mx-auto"></div>
          </div>

          <div class="timeline">
            <div v-for="exp in experiences" :key="exp.id" class="timeline-item">
              <div class="timeline-dot">
                <svg v-if="exp.type === 'education'" xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 10v6M2 10l10-5 10 5-10 5z"></path><path d="M6 12v5c3 3 9 3 12 0v-5"></path></svg>
                <svg v-else xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="7" width="20" height="14" rx="2" ry="2"></rect><path d="M16 21V5a2 2 0 0 0-2-2h-4a2 2 0 0 0-2 2v16"></path></svg>
              </div>
              <div class="timeline-content">
                <span class="timeline-period">{{ exp.period }}</span>
                <h3 class="timeline-role">{{ exp.role }}</h3>
                <h4 class="timeline-company">{{ exp.company }}</h4>
                <p class="timeline-desc">{{ exp.desc }}</p>
              </div>
            </div>
          </div>
        </div>
      </section>
      
      <section id="projects" class="projects">
        <div class="container">
          <div class="section-header">
            <p class="section-tag">{{ t.projects.tag }}</p>
            <h2 class="section-title">{{ t.projects.title }}</h2>
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
          <h2 class="cta-title">{{ t.cta.title }}</h2>
          <p class="cta-desc">{{ t.cta.desc }}</p>
          <div class="cta-buttons">
            <a :href="'mailto:' + contact.email" class="btn btn-primary cta-btn">
              <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"></path><polyline points="22,6 12,13 2,6"></polyline></svg>
              {{ t.cta.btnEmail }}
            </a>
            <a :href="contact.linkedin" target="_blank" class="btn btn-secondary cta-btn">{{ t.cta.btnLinkedIn }}</a>
          </div>
        </div>
      </section>
    </main>

    <footer class="footer">
      <div class="container footer-inner">
        <p class="copyright">© 2026 Abid Azis. {{ t.footer.text }} <span class="vue-icon">V</span> Vue.js & Vite.</p>
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
            
            <div v-if="selectedProject.metric" style="background: rgba(34, 211, 238, 0.05); border-left: 4px solid var(--accent); padding: 15px; border-radius: 4px; margin-bottom: 25px;">
              <h4 style="color: var(--accent); font-weight: 700; font-size: 0.9rem; text-transform: uppercase; margin-bottom: 5px; letter-spacing: 0.5px;">{{ t.modal.impact }}</h4>
              <p style="color: #fff; font-size: 1rem; font-weight: 500;">✨ {{ selectedProject.metric }}</p>
            </div>

            <div class="modal-desc">
              <h3>{{ t.modal.desc }}</h3>
              <p>{{ selectedProject.fullDesc }}</p>
            </div>

            <div v-if="selectedProject.contributions && selectedProject.contributions.length" style="margin-bottom: 30px;">
              <h3 style="color: #fff; margin-bottom: 12px; font-size: 1.2rem; font-weight: 700;">{{ t.modal.contrib }}</h3>
              <ul style="list-style-type: none; padding-left: 0; display: flex; flex-direction: column; gap: 10px;">
                <li v-for="(task, i) in selectedProject.contributions" :key="i" style="display: flex; gap: 10px; color: #cbd5e1; font-size: 0.95rem; line-height: 1.6;">
                  <span style="color: var(--accent)">▹</span>
                  <span>{{ task }}</span>
                </li>
              </ul>
            </div>
            
            <div class="modal-actions">
              <a v-if="selectedProject.link !== '#'" :href="selectedProject.link" target="_blank" class="btn btn-primary btn-sm">{{ t.modal.demo }}</a>
              <a v-if="selectedProject.github !== '#'" :href="selectedProject.github" target="_blank" class="btn btn-secondary btn-sm">{{ t.modal.source }}</a>
            </div>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<style scoped>
/* Tombol Bahasa (Language Toggle) Styling */
.lang-toggle {
  background: rgba(34, 211, 238, 0.05);
  border: 1px solid rgba(34, 211, 238, 0.3);
  color: var(--accent);
  padding: 6px 12px;
  border-radius: 6px;
  font-weight: 700;
  font-size: 0.85rem;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  gap: 6px;
}
.lang-toggle:hover {
  background: var(--accent);
  color: #070a13;
  box-shadow: 0 0 10px rgba(34, 211, 238, 0.4);
}
.mobile-lang-btn {
  padding: 4px 10px;
  font-size: 0.8rem;
}

.hamburger-menu {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 24px;
  height: 18px;
  background: transparent;
  border: none;
  cursor: pointer;
  padding: 0;
  z-index: 101;
}
.hamburger-menu .bar {
  width: 100%;
  height: 2px;
  background-color: #fff;
  transition: all 0.3s ease;
}
.rotate-top { transform: translateY(8px) rotate(45deg); }
.fade-out { opacity: 0; }
.rotate-bottom { transform: translateY(-8px) rotate(-45deg); }

@media (min-width: 768px) {
  .desktop-only { display: flex !important; }
  .md-hidden { display: none !important; }
}
@media (max-width: 767px) {
  .desktop-only { display: none !important; }
  .md-hidden { display: flex !important; }
}

.mobile-nav-dropdown {
  display: flex;
  flex-direction: column;
  position: absolute;
  top: 100%;
  left: 0;
  width: 100%;
  background-color: #0f1626;
  border-bottom: 1px solid #17223b;
  padding: 1rem 1.5rem;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.3);
  z-index: 99;
}
.mobile-nav-dropdown a {
  padding: 0.75rem 0;
  font-weight: 500;
  color: #94a3b8;
  border-bottom: 1px solid #17223b;
}
.mobile-nav-dropdown a:last-child { border-bottom: none; }
.mobile-nav-dropdown a:hover { color: var(--accent); }
.mobile-nav-dropdown .mobile-nav-cta {
  margin-top: 0.5rem; color: var(--accent); font-weight: 600; text-align: center;
  background: rgba(34, 211, 238, 0.05); border: 1px solid rgba(34, 211, 238, 0.2); border-radius: 0.375rem; padding: 0.5rem;
}

.slide-down-enter-active, .slide-down-leave-active { transition: all 0.3s ease-out; }
.slide-down-enter-from, .slide-down-leave-to { transform: translateY(-10px); opacity: 0; }
</style>