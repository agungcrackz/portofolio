<template>
  <section id="projects" class="projects">
    <div class="container">
      <h2 class="section-title">Projects</h2>
      <div class="projects-grid">
        <div 
          v-for="project in projects" 
          :key="project.id"
          class="project-card"
        >
          <div class="project-image">
            <div class="project-placeholder">{{ project.icon }}</div>
          </div>
          <div class="project-content">
            <h3>{{ project.title }}</h3>
            <p>{{ project.description }}</p>
            <div class="project-tech">
              <span 
                v-for="tech in project.technologies" 
                :key="tech"
                class="tech-tag"
              >
                {{ tech }}
              </span>
            </div>
            <div class="project-links">
              <a :href="project.demo" class="btn btn-demo" target="_blank">
                Live Demo
              </a>
              <a :href="project.github" class="btn btn-code" target="_blank">
                View Code
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue'

interface Project {
  id: number
  title: string
  description: string
  technologies: string[]
  demo: string
  github: string
  icon: string
}

// Ganti projects ini dengan project kamu yang sebenarnya
const projects = ref<Project[]>([
  {
    id: 1,
    title: 'E-Commerce Website',
    description: 'Website e-commerce modern dengan fitur cart, payment gateway, dan admin dashboard.',
    technologies: ['Vue.js', 'TypeScript', 'Tailwind CSS', 'Node.js'],
    demo: '#',
    github: '#',
    icon: '🛒'
  },
  {
    id: 2,
    title: 'Task Management App',
    description: 'Aplikasi manajemen tugas dengan drag & drop, real-time updates, dan team collaboration.',
    technologies: ['React', 'Firebase', 'Material-UI', 'TypeScript'],
    demo: '#',
    github: '#',
    icon: '📋'
  },
  {
    id: 3,
    title: 'Weather Dashboard',
    description: 'Dashboard cuaca dengan data real-time, forecast 7 hari, dan visualisasi interaktif.',
    technologies: ['Vue.js', 'Chart.js', 'OpenWeather API', 'CSS3'],
    demo: '#',
    github: '#',
    icon: '🌤️'
  },
  {
    id: 4,
    title: 'Portfolio Website',
    description: 'Website portfolio responsive dengan animasi smooth dan design modern.',
    technologies: ['Vue.js', 'TypeScript', 'SCSS', 'Vite'],
    demo: '#',
    github: '#',
    icon: '💼'
  }
])
</script>

<style scoped>
.projects {
  padding: 100px 0;
  background: #0f172a;
  position: relative;
}

.projects::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: 
    radial-gradient(circle at 20% 20%, rgba(59, 130, 246, 0.05) 0%, transparent 50%),
    radial-gradient(circle at 80% 80%, rgba(139, 92, 246, 0.05) 0%, transparent 50%);
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

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2rem;
}

.project-card {
  background: rgba(30, 41, 59, 0.5);
  backdrop-filter: blur(10px);
  border-radius: 20px;
  overflow: hidden;
  border: 1px solid rgba(148, 163, 184, 0.1);
  transition: all 0.3s ease;
}

.project-card:hover {
  transform: translateY(-10px);
  border-color: rgba(59, 130, 246, 0.3);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
}

.project-image {
  height: 200px;
  background: linear-gradient(135deg, #3b82f6 0%, #8b5cf6 100%);
  display: flex;
  align-items: center;
  justify-content: center;
}

.project-placeholder {
  font-size: 4rem;
}

.project-content {
  padding: 2rem;
}

.project-content h3 {
  font-size: 1.5rem;
  margin-bottom: 1rem;
  color: #f8fafc;
}

.project-content p {
  color: #94a3b8;
  line-height: 1.6;
  margin-bottom: 1.5rem;
}

.project-tech {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
}

.tech-tag {
  background: rgba(59, 130, 246, 0.1);
  color: #3b82f6;
  padding: 0.3rem 0.8rem;
  border-radius: 15px;
  font-size: 0.8rem;
  font-weight: 500;
  border: 1px solid rgba(59, 130, 246, 0.2);
}

.project-links {
  display: flex;
  gap: 1rem;
}

.btn {
  padding: 0.7rem 1.5rem;
  border: none;
  border-radius: 25px;
  text-decoration: none;
  font-weight: 600;
  transition: all 0.3s ease;
  cursor: pointer;
}

.btn-demo {
  background: linear-gradient(135deg, #3b82f6 0%, #8b5cf6 100%);
  color: white;
  border: 2px solid transparent;
}

.btn-demo:hover {
  background: linear-gradient(135deg, #2563eb 0%, #7c3aed 100%);
  transform: translateY(-2px);
}

.btn-code {
  background: transparent;
  color: #3b82f6;
  border: 2px solid #3b82f6;
}

.btn-code:hover {
  background: #3b82f6;
  color: white;
}

@media (max-width: 768px) {
  .projects {
    padding: 60px 0;
  }
  
  .section-title {
    font-size: 2rem;
  }
  
  .projects-grid {
    grid-template-columns: 1fr;
  }
  
  .project-links {
    flex-direction: column;
  }
}
</style>