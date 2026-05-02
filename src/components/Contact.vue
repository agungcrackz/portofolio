<template>
  <section id="contact" class="contact">
    <div class="container">
      <h2 class="section-title">Hubungi Saya</h2>
      <div class="contact-content">
        <div class="contact-info">
          <h3>Mari Berkolaborasi!</h3>
          <p>Saya selalu terbuka untuk diskusi project baru, peluang kerja, atau sekadar ngobrol tentang teknologi.</p>
          
          <div class="contact-methods">
            <div class="contact-item">
              <div class="contact-icon">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                  <path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/>
                </svg>
              </div>
              <div>
                <h4>Email</h4>
                <p>{{ email }}</p>
              </div>
            </div>
            <div class="contact-item">
              <div class="contact-icon">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                  <path d="M6.62 10.79c1.44 2.83 3.76 5.14 6.59 6.59l2.2-2.2c.27-.27.67-.36 1.02-.24 1.12.37 2.33.57 3.57.57.55 0 1 .45 1 1V20c0 .55-.45 1-1 1-9.39 0-17-7.61-17-17 0-.55.45-1 1-1h3.5c.55 0 1 .45 1 1 0 1.25.2 2.45.57 3.57.11.35.03.74-.25 1.02l-2.2 2.2z"/>
                </svg>
              </div>
              <div>
                <h4>Phone</h4>
                <p>{{ phone }}</p>
              </div>
            </div>
            <div class="contact-item">
              <div class="contact-icon">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                  <path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7zm0 9.5c-1.38 0-2.5-1.12-2.5-2.5s1.12-2.5 2.5-2.5 2.5 1.12 2.5 2.5-1.12 2.5-2.5 2.5z"/>
                </svg>
              </div>
              <div>
                <h4>Location</h4>
                <p>{{ location }}</p>
              </div>
            </div>
          </div>

          <div class="social-links">
            <a v-for="social in socialLinks" :key="social.name" :href="social.url" class="social-link" target="_blank">
              <div class="social-icon">
                <!-- GitHub Icon -->
                <svg v-if="social.icon === 'github'" width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
                  <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
                </svg>
                
                <!-- LinkedIn Icon -->
                <svg v-else-if="social.icon === 'linkedin'" width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
                  <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
                </svg>
                
                <!-- Instagram Icon -->
                <svg v-else-if="social.icon === 'instagram'" width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
                  <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/>
                </svg>
                
                <!-- Twitter Icon -->
                <svg v-else-if="social.icon === 'twitter'" width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
                  <path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.17-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/>
                </svg>
              </div>
              {{ social.name }}
            </a>
          </div>
        </div>

        <form @submit.prevent="submitForm" class="contact-form">
          <div class="form-group">
            <input 
              v-model="form.name" 
              name="name"
              type="text" 
              placeholder="Nama Lengkap" 
              required
            >
          </div>
          <div class="form-group">
            <input 
              v-model="form.email" 
              name="email"
              type="email" 
              placeholder="Email" 
              required
            >
          </div>
          <div class="form-group">
            <input 
              v-model="form.subject" 
              name="subject"
              type="text" 
              placeholder="Subject" 
              required
            >
          </div>
          <div class="form-group">
            <textarea 
              v-model="form.message" 
              name="message"
              placeholder="Pesan Anda" 
              rows="5" 
              required
            ></textarea>
          </div>
          <button type="submit" class="btn btn-submit" :disabled="isSubmitting">
            {{ isSubmitting ? 'Mengirim...' : 'Kirim Pesan' }}
          </button>
        </form>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref, reactive } from 'vue'

// Ganti contact info ini dengan info kamu
const email = ref('agungcrackz@gmail.com')
const phone = ref('+62 851-3392-4450')
const location = ref('Langkat, Indonesia')

const socialLinks = ref([
  { name: 'GitHub', url: 'https://github.com/agungcrackz', icon: 'github' },
  { name: 'LinkedIn', url: 'https://linkedin.com/in/username', icon: 'linkedin' },
  { name: 'Instagram', url: 'https://instagram.com/agungcrackz', icon: 'instagram' },
  { name: 'Twitter', url: 'https://twitter.com/username', icon: 'twitter' }
])

const form = reactive({
  name: '',
  email: '',
  subject: '',
  message: ''
})

const isSubmitting = ref(false)

// PENTING: Ganti FORMSPREE_ID dengan Form ID kamu dari https://formspree.io/
// Contoh: 'f/mojrjaro' atau 'f/xxxxxxxx'
const FORMSPREE_ID = 'f/mojrjaro'

const submitForm = async () => {
  // Check if Formspree is configured
  if (!FORMSPREE_ID) {
    alert('⚠️ Formspree belum dikonfigurasi!\n\n📋 Langkah Setup:\n1. Buka https://formspree.io/\n2. Sign up dengan email: agungcrackz@gmail.com\n3. Buat form baru\n4. Copy Form ID (contoh: f/xxxxxxxx)\n5. Update FORMSPREE_ID di src/components/Contact.vue\n\n📧 Untuk sekarang, hubungi langsung:\nagungcrackz@gmail.com\n📱 +62 851-3392-4450')
    return
  }

  isSubmitting.value = true
  
  try {
    const response = await fetch(`https://formspree.io/${FORMSPREE_ID}`, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({
        name: form.name,
        email: form.email,
        subject: form.subject,
        message: form.message
      })
    })

    if (response.ok) {
      alert('✅ Pesan berhasil dikirim!\n\nTerima kasih, saya akan segera membalas pesan Anda.')
      
      // Reset form
      form.name = ''
      form.email = ''
      form.subject = ''
      form.message = ''
    } else {
      throw new Error('Response not ok')
    }
  } catch (error) {
    console.error('Error:', error)
    alert('❌ Gagal mengirim pesan.\n\nSilakan hubungi langsung:\n📧 agungcrackz@gmail.com\n📱 +62 851-3392-4450')
  } finally {
    isSubmitting.value = false
  }
}
</script>

<style scoped>
.contact {
  padding: 100px 0;
  background: linear-gradient(135deg, #1e293b 0%, #0f172a 100%);
  color: white;
  position: relative;
}

.contact::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: 
    radial-gradient(circle at 20% 80%, rgba(59, 130, 246, 0.1) 0%, transparent 50%),
    radial-gradient(circle at 80% 20%, rgba(139, 92, 246, 0.1) 0%, transparent 50%);
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

.contact-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: start;
}

.contact-info h3 {
  font-size: 1.8rem;
  margin-bottom: 1rem;
}

.contact-info > p {
  font-size: 1.1rem;
  opacity: 0.9;
  margin-bottom: 2rem;
  line-height: 1.6;
}

.contact-methods {
  margin-bottom: 2rem;
}

.contact-item {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-bottom: 1.5rem;
}

.contact-icon {
  width: 50px;
  height: 50px;
  background: rgba(59, 130, 246, 0.1);
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid rgba(59, 130, 246, 0.2);
  transition: all 0.3s ease;
}

.contact-icon svg {
  color: #3b82f6;
  transition: all 0.3s ease;
}

.contact-item:hover .contact-icon {
  background: #3b82f6;
  border-color: #3b82f6;
  transform: scale(1.05);
}

.contact-item:hover .contact-icon svg {
  color: white;
}

.contact-item h4 {
  margin-bottom: 0.2rem;
  font-size: 1.1rem;
}

.contact-item p {
  opacity: 0.8;
}

.social-links {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}

.social-link {
  display: flex;
  align-items: center;
  gap: 0.8rem;
  padding: 0.8rem 1.5rem;
  background: rgba(30, 41, 59, 0.5);
  backdrop-filter: blur(10px);
  border-radius: 25px;
  text-decoration: none;
  color: white;
  transition: all 0.3s ease;
  border: 1px solid rgba(148, 163, 184, 0.1);
}

.social-link:hover {
  background: rgba(30, 41, 59, 0.8);
  border-color: rgba(59, 130, 246, 0.3);
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.2);
}

.social-link span {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 32px;
  height: 32px;
  background: rgba(59, 130, 246, 0.1);
  border-radius: 8px;
  font-size: 1.2rem;
  border: 1px solid rgba(59, 130, 246, 0.2);
}

/* Social Media Icons */
.social-icon {
  width: 32px;
  height: 32px;
  border-radius: 8px;
  position: relative;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(59, 130, 246, 0.1);
  border: 1px solid rgba(59, 130, 246, 0.2);
}

.social-icon svg {
  width: 20px;
  height: 20px;
  color: #94a3b8;
  transition: all 0.3s ease;
}

/* Platform-specific colors on hover */
.social-link:hover .social-icon svg {
  color: white;
}

.social-link:hover .social-icon {
  background: var(--social-color, #3b82f6);
  border-color: var(--social-color, #3b82f6);
  transform: scale(1.1);
}

/* GitHub */
.social-link:nth-child(1) {
  --social-color: #333;
}

/* LinkedIn */
.social-link:nth-child(2) {
  --social-color: #0077b5;
}

/* Instagram */
.social-link:nth-child(3) {
  --social-color: #e4405f;
}

/* Twitter */
.social-link:nth-child(4) {
  --social-color: #1da1f2;
}

.contact-form {
  background: rgba(30, 41, 59, 0.5);
  backdrop-filter: blur(10px);
  padding: 2rem;
  border-radius: 20px;
  border: 1px solid rgba(148, 163, 184, 0.1);
}

.form-group {
  margin-bottom: 1.5rem;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 1rem;
  border: 1px solid rgba(148, 163, 184, 0.2);
  border-radius: 10px;
  background: rgba(15, 23, 42, 0.5);
  color: #f8fafc;
  font-size: 1rem;
  transition: all 0.3s ease;
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: #3b82f6;
  box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
}

.btn-submit {
  width: 100%;
  padding: 1rem;
  background: linear-gradient(135deg, #3b82f6 0%, #8b5cf6 100%);
  color: white;
  border: none;
  border-radius: 10px;
  font-size: 1.1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
}

.btn-submit:hover:not(:disabled) {
  background: linear-gradient(135deg, #2563eb 0%, #7c3aed 100%);
  transform: translateY(-2px);
}

.btn-submit:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}

@media (max-width: 768px) {
  .contact {
    padding: 60px 0;
  }
  
  .section-title {
    font-size: 2rem;
  }
  
  .contact-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
  
  .social-links {
    justify-content: center;
  }
}
</style>