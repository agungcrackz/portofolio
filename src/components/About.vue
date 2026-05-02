<template>
  <section id="about" class="about">
    <div class="container">
      <h2 class="section-title">Tentang Saya</h2>
      <div class="about-content">
        <div class="about-text">
          <p>{{ aboutText }}</p>
          <div class="stats">
            <div class="stat-item">
              <h3>{{ projectsCount }}+</h3>
              <p>Projects Completed</p>
            </div>
            <div class="stat-item">
              <h3>{{ experienceYears }}+</h3>
              <p>Years Experience</p>
            </div>
            <div class="stat-item">
              <h3>{{ clientsCount }}+</h3>
              <p>Happy Clients</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue'

// Ganti data ini sesuai dengan info kamu
const aboutText = ref(`
  Saya adalah seorang Frontend Developer yang passionate dalam menciptakan pengalaman web yang luar biasa. 
  Dengan pengalaman dalam berbagai teknologi modern, saya selalu berusaha untuk mengikuti perkembangan terbaru 
  dalam dunia web development. Saya percaya bahwa kombinasi antara desain yang menarik dan kode yang clean 
  adalah kunci untuk menciptakan aplikasi web yang sukses.
`)

const projectsCount = ref(25)
const experienceYears = ref(3)
const clientsCount = ref(15)
</script>

<style scoped>
.about {
  padding: 100px 0;
  background: #1e293b;
  position: relative;
}

.about::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: 
    radial-gradient(circle at 80% 20%, rgba(59, 130, 246, 0.05) 0%, transparent 50%),
    radial-gradient(circle at 20% 80%, rgba(139, 92, 246, 0.05) 0%, transparent 50%);
  pointer-events: none;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

.section-title {
  text-align: center;
  font-size: 2.5rem;
  margin-bottom: 3rem;
  background: linear-gradient(135deg, #3b82f6 0%, #8b5cf6 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.about-content {
  display: grid;
  gap: 3rem;
  align-items: center;
}

.about-text p {
  font-size: 1.1rem;
  line-height: 1.8;
  color: #94a3b8;
  margin-bottom: 2rem;
}

.stats {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 2rem;
  margin-top: 2rem;
}

.stat-item {
  text-align: center;
  padding: 1.5rem;
  background: rgba(30, 41, 59, 0.5);
  backdrop-filter: blur(10px);
  border-radius: 15px;
  border: 1px solid rgba(148, 163, 184, 0.1);
  transition: transform 0.3s ease;
}

.stat-item:hover {
  transform: translateY(-5px);
  border-color: rgba(59, 130, 246, 0.3);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
}

.stat-item h3 {
  font-size: 2rem;
  background: linear-gradient(135deg, #3b82f6 0%, #8b5cf6 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 0.5rem;
}

.stat-item p {
  color: #94a3b8;
  font-weight: 500;
}

@media (max-width: 768px) {
  .about {
    padding: 60px 0;
  }
  
  .section-title {
    font-size: 2rem;
  }
  
  .stats {
    grid-template-columns: 1fr;
  }
}
</style>