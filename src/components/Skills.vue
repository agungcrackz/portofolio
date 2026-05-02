<template>
  <section id="skills" class="skills">
    <div class="container">
      <!-- Header -->
      <div class="skills-header">
        <h2 class="section-title">Skills & Expertise</h2>
        <p class="section-subtitle">Technologies I work with to bring ideas to life</p>
      </div>

      <!-- Skills Grid -->
      <div class="skills-grid">
        <div 
          v-for="skill in skills" 
          :key="skill.name"
          class="skill-card"
          :style="{ '--skill-color': skill.color }"
        >
          <div class="skill-content">
            <div class="skill-header">
              <h3 class="skill-name">{{ skill.name }}</h3>
              <span class="skill-percentage">{{ skill.level }}%</span>
            </div>
            
            <div class="skill-bar">
              <div 
                class="skill-progress" 
                :style="{ width: (skill.animatedLevel || 0) + '%' }"
              ></div>
            </div>
            
            <div class="skill-meta">
              <span class="skill-category">{{ skill.category }}</span>
              <span class="skill-experience">{{ skill.experience }}</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Summary Stats -->
      <div class="skills-summary">
        <div class="summary-stats">
          <div class="stat">
            <div class="stat-number">{{ totalSkills }}</div>
            <div class="stat-label">Technologies</div>
          </div>
          <div class="stat">
            <div class="stat-number">{{ averageLevel }}%</div>
            <div class="stat-label">Average Proficiency</div>
          </div>
          <div class="stat">
            <div class="stat-number">{{ yearsExperience }}+</div>
            <div class="stat-label">Years Experience</div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, computed, onMounted, onUnmounted } from 'vue'

interface Skill {
  name: string
  level: number
  color: string
  category: string
  experience: string
  animatedLevel?: number
}

// Skills data - ganti sesuai kemampuan kamu
const skills = ref<Skill[]>([
  { name: 'Vue.js', level: 90, color: '#4FC08D', category: 'Frontend', experience: '2+ years', animatedLevel: 0 },
  { name: 'JavaScript', level: 88, color: '#F7DF1E', category: 'Frontend', experience: '3+ years', animatedLevel: 0 },
  { name: 'TypeScript', level: 85, color: '#3178C6', category: 'Frontend', experience: '2+ years', animatedLevel: 0 },
  { name: 'React', level: 78, color: '#61DAFB', category: 'Frontend', experience: '1.5+ years', animatedLevel: 0 },
  { name: 'HTML/CSS', level: 95, color: '#E34F26', category: 'Frontend', experience: '4+ years', animatedLevel: 0 },
  { name: 'Tailwind CSS', level: 90, color: '#06B6D4', category: 'Frontend', experience: '1.5+ years', animatedLevel: 0 },
  { name: 'Node.js', level: 75, color: '#339933', category: 'Backend', experience: '2+ years', animatedLevel: 0 },
  { name: 'MongoDB', level: 70, color: '#47A248', category: 'Backend', experience: '1+ years', animatedLevel: 0 },
  { name: 'Git', level: 88, color: '#F05032', category: 'Tools', experience: '3+ years', animatedLevel: 0 },
  { name: 'Figma', level: 82, color: '#F24E1E', category: 'Design', experience: '2+ years', animatedLevel: 0 },
  { name: 'Vite', level: 85, color: '#646CFF', category: 'Tools', experience: '1+ years', animatedLevel: 0 },
  { name: 'SCSS', level: 87, color: '#CF649A', category: 'Frontend', experience: '2+ years', animatedLevel: 0 }
])

let observer: IntersectionObserver | null = null
let hasAnimated = false

// Computed properties
const totalSkills = computed(() => skills.value.length)

const averageLevel = computed(() => {
  const total = skills.value.reduce((sum, skill) => sum + skill.level, 0)
  return Math.round(total / skills.value.length)
})

const yearsExperience = ref(3)

// Animate progress bars when section is visible
const animateSkills = () => {
  skills.value.forEach((skill) => {
    skill.animatedLevel = skill.level
  })
}

onMounted(() => {
  const skillsSection = document.getElementById('skills')
  
  if (skillsSection) {
    observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting && !hasAnimated) {
            hasAnimated = true
            animateSkills()
            observer?.unobserve(skillsSection)
          }
        })
      },
      { threshold: 0.2 }
    )
    
    observer.observe(skillsSection)
  }
})

onUnmounted(() => {
  if (observer) {
    observer.disconnect()
  }
})
</script>

<style scoped>
.skills {
  padding: 100px 0;
  background: #0f172a;
  position: relative;
}

.skills::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: 
    radial-gradient(circle at 20% 80%, rgba(59, 130, 246, 0.1) 0%, transparent 50%),
    radial-gradient(circle at 80% 20%, rgba(139, 92, 246, 0.1) 0%, transparent 50%),
    radial-gradient(circle at 40% 40%, rgba(16, 185, 129, 0.05) 0%, transparent 50%);
  pointer-events: none;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
  position: relative;
  z-index: 1;
}

/* Header */
.skills-header {
  text-align: center;
  margin-bottom: 4rem;
}

.section-title {
  font-size: 2.5rem;
  font-weight: 700;
  color: #f8fafc;
  margin-bottom: 1rem;
  background: linear-gradient(135deg, #3b82f6 0%, #8b5cf6 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.section-subtitle {
  font-size: 1.1rem;
  color: #94a3b8;
  max-width: 600px;
  margin: 0 auto;
}

/* Skills Grid */
.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 1.5rem;
  margin-bottom: 4rem;
}

.skill-card {
  background: rgba(30, 41, 59, 0.5);
  backdrop-filter: blur(10px);
  border-radius: 16px;
  padding: 1.5rem;
  border: 1px solid rgba(148, 163, 184, 0.1);
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  overflow: hidden;
}

.skill-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 2px;
  background: linear-gradient(90deg, var(--skill-color), transparent);
  opacity: 0;
  transition: opacity 0.3s ease;
}

.skill-card::after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, var(--skill-color), transparent);
  opacity: 0;
  transition: opacity 0.3s ease;
  z-index: -1;
}

.skill-card:hover {
  transform: translateY(-8px);
  border-color: rgba(var(--skill-color-rgb, 59, 130, 246), 0.3);
  box-shadow: 
    0 20px 25px -5px rgba(0, 0, 0, 0.3),
    0 10px 10px -5px rgba(0, 0, 0, 0.2),
    0 0 0 1px rgba(var(--skill-color-rgb, 59, 130, 246), 0.1);
}

.skill-card:hover::before {
  opacity: 1;
}

.skill-card:hover::after {
  opacity: 0.03;
}

.skill-content {
  position: relative;
  z-index: 1;
}

.skill-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1rem;
}

.skill-name {
  font-size: 1.1rem;
  font-weight: 600;
  color: #f8fafc;
  margin: 0;
}

.skill-percentage {
  font-size: 0.9rem;
  font-weight: 700;
  color: var(--skill-color);
  background: rgba(30, 41, 59, 0.8);
  padding: 0.3rem 0.7rem;
  border-radius: 8px;
  border: 1px solid rgba(148, 163, 184, 0.1);
}

.skill-bar {
  width: 100%;
  height: 8px;
  background: rgba(30, 41, 59, 0.8);
  border-radius: 4px;
  overflow: hidden;
  margin-bottom: 1rem;
  border: 1px solid rgba(148, 163, 184, 0.1);
}

.skill-progress {
  height: 100%;
  background: linear-gradient(90deg, var(--skill-color), var(--skill-color));
  border-radius: 4px;
  transition: width 2s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  box-shadow: 0 0 10px rgba(var(--skill-color-rgb, 59, 130, 246), 0.3);
}

.skill-progress::after {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
  animation: shimmer 3s infinite;
}

@keyframes shimmer {
  0% { left: -100%; }
  100% { left: 100%; }
}

.skill-meta {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.skill-category {
  font-size: 0.8rem;
  color: #94a3b8;
  background: rgba(30, 41, 59, 0.6);
  padding: 0.3rem 0.7rem;
  border-radius: 6px;
  font-weight: 500;
  border: 1px solid rgba(148, 163, 184, 0.1);
}

.skill-experience {
  font-size: 0.8rem;
  color: #64748b;
  font-weight: 500;
}

/* Summary Stats */
.skills-summary {
  background: rgba(30, 41, 59, 0.5);
  backdrop-filter: blur(10px);
  border-radius: 16px;
  padding: 2.5rem;
  border: 1px solid rgba(148, 163, 184, 0.1);
  position: relative;
  overflow: hidden;
}

.skills-summary::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, rgba(59, 130, 246, 0.05) 0%, rgba(139, 92, 246, 0.05) 100%);
  pointer-events: none;
}

.summary-stats {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 2rem;
  text-align: center;
  position: relative;
  z-index: 1;
}

.stat {
  padding: 1.5rem;
  background: rgba(15, 23, 42, 0.3);
  border-radius: 12px;
  border: 1px solid rgba(148, 163, 184, 0.1);
  transition: all 0.3s ease;
}

.stat:hover {
  transform: translateY(-4px);
  border-color: rgba(59, 130, 246, 0.3);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
}

.stat-number {
  font-size: 2.5rem;
  font-weight: 800;
  background: linear-gradient(135deg, #3b82f6 0%, #8b5cf6 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 0.5rem;
  line-height: 1;
}

.stat-label {
  font-size: 0.9rem;
  color: #94a3b8;
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

/* Responsive */
@media (max-width: 768px) {
  .skills {
    padding: 60px 0;
  }
  
  .section-title {
    font-size: 2rem;
  }
  
  .skills-grid {
    grid-template-columns: 1fr;
  }
  
  .summary-stats {
    grid-template-columns: repeat(2, 1fr);
    gap: 1rem;
  }
  
  .container {
    padding: 0 1rem;
  }
}

@media (max-width: 480px) {
  .summary-stats {
    grid-template-columns: 1fr;
  }
  
  .skill-header {
    flex-direction: column;
    align-items: flex-start;
    gap: 0.5rem;
  }
  
  .skill-meta {
    flex-direction: column;
    align-items: flex-start;
    gap: 0.5rem;
  }
  
  .skills-summary {
    padding: 1.5rem;
  }
}

/* Skill Color Variables */
.skill-card:nth-child(1) { --skill-color-rgb: 79, 192, 141; }
.skill-card:nth-child(2) { --skill-color-rgb: 247, 223, 30; }
.skill-card:nth-child(3) { --skill-color-rgb: 49, 120, 198; }
.skill-card:nth-child(4) { --skill-color-rgb: 97, 218, 251; }
.skill-card:nth-child(5) { --skill-color-rgb: 227, 79, 38; }
.skill-card:nth-child(6) { --skill-color-rgb: 6, 182, 212; }
.skill-card:nth-child(7) { --skill-color-rgb: 51, 153, 51; }
.skill-card:nth-child(8) { --skill-color-rgb: 71, 162, 72; }
.skill-card:nth-child(9) { --skill-color-rgb: 240, 80, 50; }
.skill-card:nth-child(10) { --skill-color-rgb: 242, 78, 30; }
.skill-card:nth-child(11) { --skill-color-rgb: 100, 108, 255; }
.skill-card:nth-child(12) { --skill-color-rgb: 207, 100, 154; }
</style>