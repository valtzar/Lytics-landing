<template>
  <section class="contact" id="contact">
    <div class="container">
      <div class="contact-content">
        <h2>Ponte en Contacto</h2>
        <p class="contact-subtitle">¿Listo para transformar tu organización? Contáctanos hoy</p>
        
        <div class="email-container">
          <div class="email-box" @click="copyEmail" :class="{ copied }">
            <svg class="icon-email" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"></path>
              <polyline points="22,6 12,13 2,6"></polyline>
            </svg>
            <span class="email-text">{{ email }}</span>
            <svg v-if="!copied" class="icon-copy" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M16 4h2a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2H6a2 2 0 0 1-2-2V6a2 2 0 0 1 2-2h2"></path>
              <rect x="8" y="2" width="8" height="4" rx="1" ry="1"></rect>
            </svg>
            <svg v-else class="icon-check" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <polyline points="20 6 9 17 4 12"></polyline>
            </svg>
          </div>
          <p v-if="copied" class="copy-feedback">✓ Copiado al portapapeles</p>
        </div>

        <p class="contact-note">O envía un email directamente a <span class="email-link" @click="openEmail">{{ email }}</span></p>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Contact',
  data() {
    return {
      email: 'experiencia@lytics.cl',
      copied: false
    }
  },
  methods: {
    copyEmail() {
      navigator.clipboard.writeText(this.email).then(() => {
        this.copied = true
        setTimeout(() => {
          this.copied = false
        }, 2000)
      }).catch(err => {
        console.error('Error al copiar:', err)
      })
    },
    openEmail() {
      window.location.href = `mailto:${this.email}`
    }
  }
}
</script>

<style scoped>
.contact {
  padding: var(--spacing-3xl) 0;
  background: linear-gradient(135deg, rgba(0, 102, 204, 0.05) 0%, rgba(77, 148, 255, 0.05) 100%);
  border-top: 2px solid var(--color-primary);
}

.container {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 var(--spacing-md);
}

.contact-content {
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: var(--spacing-lg);
}

.contact-content h2 {
  font-size: var(--font-size-4xl);
  color: var(--color-black);
  margin: 0;
  font-weight: var(--font-weight-bold);
}

.contact-subtitle {
  font-size: var(--font-size-lg);
  color: var(--color-gray-600);
  margin: 0;
  max-width: 600px;
}

.email-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: var(--spacing-md);
  margin: var(--spacing-xl) 0;
}

.email-box {
  display: flex;
  align-items: center;
  gap: var(--spacing-md);
  padding: var(--spacing-lg) var(--spacing-2xl);
  background-color: var(--color-white);
  border: 2px solid var(--color-primary);
  border-radius: var(--border-radius-lg);
  cursor: pointer;
  transition: all var(--transition-fast);
  user-select: none;
}

.email-box:hover {
  box-shadow: var(--shadow-lg);
  transform: translateY(-2px);
  border-color: var(--color-primary-dark);
}

.email-box.copied {
  border-color: #10b981;
  background-color: rgba(16, 185, 129, 0.05);
}

.icon-email {
  width: 24px;
  height: 24px;
  color: var(--color-primary);
  flex-shrink: 0;
}

.email-text {
  font-size: var(--font-size-lg);
  font-weight: var(--font-weight-bold);
  color: var(--color-primary);
  letter-spacing: 0.5px;
}

.icon-copy {
  width: 20px;
  height: 20px;
  color: var(--color-gray-500);
  flex-shrink: 0;
  transition: color var(--transition-fast);
}

.email-box:hover .icon-copy {
  color: var(--color-primary);
}

.icon-check {
  width: 20px;
  height: 20px;
  color: #10b981;
  flex-shrink: 0;
}

.copy-feedback {
  font-size: var(--font-size-base);
  color: #10b981;
  font-weight: var(--font-weight-bold);
  margin: 0;
  animation: fadeIn 0.3s ease-in;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.contact-note {
  font-size: var(--font-size-base);
  color: var(--color-gray-600);
  margin: 0;
}

.email-link {
  color: var(--color-primary);
  font-weight: var(--font-weight-bold);
  cursor: pointer;
  transition: color var(--transition-fast);
}

.email-link:hover {
  color: var(--color-primary-dark);
  text-decoration: underline;
}

html[data-theme="dark"] .email-box {
  background-color: var(--color-gray-800);
  border-color: var(--color-primary);
}

html[data-theme="dark"] .contact-content h2 {
  color: var(--color-white);
}

html[data-theme="dark"] .contact-subtitle {
  color: var(--color-gray-400);
}

html[data-theme="dark"] .contact-note {
  color: var(--color-gray-400);
}

@media (max-width: 768px) {
  .contact {
    padding: var(--spacing-2xl) 0;
  }

  .contact-content h2 {
    font-size: var(--font-size-3xl);
  }

  .email-box {
    width: 100%;
    padding: var(--spacing-md) var(--spacing-lg);
    flex-wrap: wrap;
    justify-content: center;
  }

  .email-text {
    font-size: var(--font-size-base);
  }

  .contact-note {
    font-size: var(--font-size-sm);
  }
}
</style>
