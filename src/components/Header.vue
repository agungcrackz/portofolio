<template>
  <header class="header" :class="{ 'scrolled': isScrolled }">
    <nav class="nav">
      <div class="nav-brand">
        <div class="logo">
          <span class="logo-icon">⚡</span>
          <h2 class="logo-text">
            <span class="logo-main">CV</span><span class="logo-accent"> (Curriculum Vitae)</span>
          </h2>
        </div>
      </div>
      
      <!-- Desktop Menu -->
      <ul class="nav-menu desktop-menu">
        <li v-for="item in menuItems" :key="item.id">
          <a 
            :href="item.href" 
            @click="scrollTo(item.target)"
            :class="{ 'active': activeSection === item.target }"
            class="nav-link"
          >
            {{ item.label }}
          </a>
        </li>
      </ul>

      <!-- Mobile Menu Button -->
      <button 
        class="mobile-menu-btn" 
        @click="toggleMobileMenu"
        :class="{ 'active': isMobileMenuOpen }"
      >
        <span></span>
        <span></span>
        <span></span>
      </button>

      <!-- Mobile Menu -->
      <div class="mobile-menu" :class="{ 'active': isMobileMenuOpen }">
        <ul class="mobile-nav-list">
          <li v-for="item in menuItems" :key="item.id">
            <a 
              :href="item.href" 
              @click="scrollToMobile(item.target)"
              class="mobile-nav-link"
            >
              {{ item.label }}
            </a>
          </li>
        </ul>
      </div>
    </nav>
  </header>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const activeSection = ref('home')
const isMobileMenuOpen = ref(false)

const menuItems = ref([
  { id: 1, label: 'Home', target: 'home', href: '#home' },
  { id: 2, label: 'About', target: 'about', href: '#about' },
  { id: 3, label: 'Skills', target: 'skills', href: '#skills' },
  { id: 4, label: 'Projects', target: 'projects', href: '#projects' },
  { id: 5, label: 'Contact', target: 'contact', href: '#contact' }
])

const scrollTo = (elementId: string) => {
  const element = document.getElementById(elementId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth', block: 'start' })
  }
}

const scrollToMobile = (elementId: string) => {
  scrollTo(elementId)
  isMobileMenuOpen.value = false
}

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
  
  // Update active section based on scroll position
  const sections = ['home', 'about', 'skills', 'projects', 'contact']
  const scrollPosition = window.scrollY + 100
  
  for (const section of sections) {
    const element = document.getElementById(section)
    if (element) {
      const offsetTop = element.offsetTop
      const offsetHeight = element.offsetHeight
      
      if (scrollPosition >= offsetTop && scrollPosition < offsetTop + offsetHeight) {
        activeSection.value = section
        break
      }
    }
  }
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.header {
  position: fixed;
  top: 0;
  width: 100%;
  background: rgba(15, 23, 42, 0.9);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border-bottom: 1px solid rgba(148, 163, 184, 0.1);
  z-index: 1000;
  padding: 1rem 0;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.header.scrolled {
  background: rgba(15, 23, 42, 0.95);
  backdrop-filter: blur(25px);
  -webkit-backdrop-filter: blur(25px);
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
  border-bottom: 1px solid rgba(148, 163, 184, 0.2);
  padding: 0.7rem 0;
}

.nav {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 2rem;
}

.logo {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  cursor: pointer;
  transition: transform 0.3s ease;
}

.logo:hover {
  transform: scale(1.05);
}

.logo-icon {
  font-size: 2rem;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.1); }
}

.logo-text {
  font-size: 1.5rem;
  font-weight: 800;
  letter-spacing: -0.5px;
}

.logo-main {
  background: linear-gradient(135deg, #3b82f6 0%, #8b5cf6 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.logo-accent {
  color: #10b981;
  text-shadow: 0 0 10px rgba(16, 185, 129, 0.3);
}

.desktop-menu {
  display: flex;
  list-style: none;
  gap: 0.5rem;
}

.nav-link {
  display: flex;
  align-items: center;
  text-decoration: none;
  color: #f8fafc;
  font-weight: 600;
  padding: 0.7rem 1.2rem;
  border-radius: 25px;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  overflow: hidden;
}

.nav-link::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, #3b82f6 0%, #8b5cf6 100%);
  transition: left 0.3s ease;
  z-index: -1;
}

.nav-link:hover::before,
.nav-link.active::before {
  left: 0;
}

.nav-link:hover,
.nav-link.active {
  color: white;
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(59, 130, 246, 0.3);
}

.mobile-menu-btn {
  display: none;
  flex-direction: column;
  justify-content: space-around;
  width: 30px;
  height: 30px;
  background: transparent;
  border: none;
  cursor: pointer;
  padding: 0;
  z-index: 10;
}

.mobile-menu-btn span {
  width: 100%;
  height: 3px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 2px;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  transform-origin: center;
}

.mobile-menu-btn.active span:nth-child(1) {
  transform: rotate(45deg) translate(7px, 7px);
}

.mobile-menu-btn.active span:nth-child(2) {
  opacity: 0;
  transform: scale(0);
}

.mobile-menu-btn.active span:nth-child(3) {
  transform: rotate(-45deg) translate(7px, -7px);
}

.mobile-menu {
  position: fixed;
  top: 0;
  right: -100%;
  width: 300px;
  height: 100vh;
  background: rgba(15, 23, 42, 0.95);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border-left: 1px solid rgba(148, 163, 184, 0.1);
  transition: right 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  z-index: 999;
  padding-top: 100px;
}

.mobile-menu.active {
  right: 0;
}

.mobile-nav-list {
  list-style: none;
  padding: 2rem;
}

.mobile-nav-list li {
  margin-bottom: 1rem;
}

.mobile-nav-link {
  display: flex;
  align-items: center;
  text-decoration: none;
  color: #f8fafc;
  font-weight: 600;
  font-size: 1.1rem;
  padding: 1rem;
  border-radius: 15px;
  transition: all 0.3s ease;
  border: 2px solid transparent;
}

.mobile-nav-link:hover {
  background: linear-gradient(135deg, #3b82f6 0%, #8b5cf6 100%);
  color: white;
  transform: translateX(10px);
  border-color: rgba(255, 255, 255, 0.3);
}

.mobile-nav-link .nav-icon {
  font-size: 1.2rem;
}

/* Responsive */
@media (max-width: 768px) {
  .desktop-menu {
    display: none;
  }
  
  .mobile-menu-btn {
    display: flex;
  }
  
  .nav {
    padding: 0 1rem;
  }
  
  .logo-text {
    font-size: 1.3rem;
  }
  
  .logo-icon {
    font-size: 1.7rem;
  }
}

@media (max-width: 480px) {
  .mobile-menu {
    width: 100%;
    right: -100%;
  }
  
  .mobile-menu.active {
    right: 0;
  }
}

/* Smooth animations */
* {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>