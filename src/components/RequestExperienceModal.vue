<template>
  <div class="modal-overlay" v-if="isOpen" @click="closeModal">
    <div class="modal-content" @click.stop>
      <div class="modal-header">
        <h2>Solicitar Experiencia Lytics</h2>
        <button class="close-btn" @click="closeModal">✕</button>
      </div>
      
      <form @submit.prevent="handleSubmit" class="experience-form">
        <div class="form-group">
          <label for="nombre">Su nombre</label>
          <input 
            type="text" 
            id="nombre" 
            v-model="formData.nombre" 
            placeholder="Tu nombre completo"
            required
          />
        </div>

        <div class="form-group">
          <label for="empresa">Empresa</label>
          <input 
            type="text" 
            id="empresa" 
            v-model="formData.empresa" 
            placeholder="Nombre de la empresa"
            required
          />
        </div>

        <div class="form-group">
          <label for="cargo">Nombre de su cargo</label>
          <input 
            type="text" 
            id="cargo" 
            v-model="formData.cargo" 
            placeholder="Tu cargo o posición"
            required
          />
        </div>

        <div class="form-group">
          <label for="telefono">Ingrese su número de contacto</label>
          <input 
            type="tel" 
            id="telefono" 
            v-model="formData.telefono" 
            placeholder="Tu número de teléfono"
            required
          />
        </div>

        <div class="form-group">
          <label for="correo">Ingrese su correo</label>
          <input 
            type="email" 
            id="correo" 
            v-model="formData.correo" 
            placeholder="Tu correo electrónico"
            required
          />
        </div>

        <div class="form-group">
          <label for="mensaje">Mensaje</label>
          <textarea 
            id="mensaje" 
            v-model="formData.mensaje" 
            placeholder="Cuéntanos más sobre tu interés en Lytics"
            rows="5"
            required
          ></textarea>
        </div>

        <div v-if="submitMessage" :class="['submit-message', submitStatus]">
          {{ submitMessage }}
        </div>

        <button type="submit" class="btn btn-primary" :disabled="isSubmitting">
          {{ isSubmitting ? 'Enviando...' : 'Enviar Solicitud' }}
        </button>
      </form>
    </div>
  </div>
</template>

<script>
import emailjs from '@emailjs/browser'

// Inicializar EmailJS con tu Public Key
// Reemplaza 'YOUR_PUBLIC_KEY' con tu clave pública de EmailJS
emailjs.init('jvGKmgBTrY7-QBqEu')

export default {
  name: 'RequestExperienceModal',
  props: {
    isOpen: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      formData: {
        nombre: '',
        empresa: '',
        cargo: '',
        telefono: '',
        correo: '',
        mensaje: ''
      },
      isSubmitting: false,
      submitMessage: '',
      submitStatus: '' // 'success' o 'error'
    }
  },
  methods: {
    closeModal() {
      this.$emit('close');
      this.resetForm();
    },
    resetForm() {
      this.formData = {
        nombre: '',
        empresa: '',
        cargo: '',
        telefono: '',
        correo: '',
        mensaje: ''
      };
      this.submitMessage = '';
      this.submitStatus = '';
    },
    async handleSubmit() {
      this.isSubmitting = true;
      
      try {
        // Enviar email usando EmailJS
        // Reemplaza 'YOUR_SERVICE_ID' y 'YOUR_TEMPLATE_ID' con tus valores de EmailJS
        const response = await emailjs.send(
          'service_ja29a0a',
          'template_shngzq7',
          {
            to_email: '911venta@gmail.com',
            from_name: this.formData.nombre,
            empresa: this.formData.empresa,
            cargo: this.formData.cargo,
            telefono: this.formData.telefono,
            correo: this.formData.correo,
            mensaje: this.formData.mensaje,
            reply_to: this.formData.correo
          }
        );

        if (response.status === 200) {
          this.submitStatus = 'success';
          this.submitMessage = '¡Solicitud enviada exitosamente! Nos pondremos en contacto pronto.';
          this.$emit('success', '¡Solicitud enviada exitosamente! Nos pondremos en contacto pronto.');
          this.resetForm();
          
          setTimeout(() => {
            this.closeModal();
          }, 2000);
        } else {
          throw new Error('Error al enviar la solicitud');
        }
      } catch (error) {
        this.submitStatus = 'error';
        this.submitMessage = 'Hubo un error al enviar tu solicitud. Por favor, intenta de nuevo.';
        this.$emit('error', 'Hubo un error al enviar tu solicitud. Por favor, intenta de nuevo.');
        console.error('Error:', error);
      } finally {
        this.isSubmitting = false;
      }
    }
  }
}
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 9999;
}

.modal-content {
  background-color: var(--color-white);
  border-radius: var(--border-radius-lg);
  box-shadow: var(--shadow-lg);
  max-width: 500px;
  width: 90%;
  max-height: 90vh;
  overflow-y: auto;
}

.modal-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: var(--spacing-lg);
  border-bottom: 1px solid var(--color-gray-100);
}

.modal-header h2 {
  margin: 0;
  font-size: var(--font-size-2xl);
  color: var(--color-gray-900);
}

.close-btn {
  background: none;
  border: none;
  font-size: var(--font-size-2xl);
  color: var(--color-gray-500);
  cursor: pointer;
  padding: 0;
  width: 32px;
  height: 32px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: color var(--transition-fast);
}

.close-btn:hover {
  color: var(--color-gray-900);
}

.experience-form {
  padding: var(--spacing-lg);
  display: flex;
  flex-direction: column;
  gap: var(--spacing-md);
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-xs);
}

.form-group label {
  font-weight: var(--font-weight-bold);
  color: var(--color-gray-700);
  font-size: var(--font-size-sm);
}

.form-group input,
.form-group textarea {
  padding: var(--spacing-sm) var(--spacing-md);
  border: 1px solid var(--color-gray-200);
  border-radius: var(--border-radius-md);
  font-family: inherit;
  font-size: var(--font-size-base);
  color: var(--color-gray-900);
  transition: border-color var(--transition-fast);
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: var(--color-primary);
  box-shadow: 0 0 0 3px rgba(var(--color-primary-rgb), 0.1);
}

.form-group textarea {
  resize: vertical;
  min-height: 120px;
}

.submit-message {
  padding: var(--spacing-md);
  border-radius: var(--border-radius-md);
  font-size: var(--font-size-sm);
  text-align: center;
}

.submit-message.success {
  background-color: #d4edda;
  color: #155724;
  border: 1px solid #c3e6cb;
}

.submit-message.error {
  background-color: #f8d7da;
  color: #721c24;
  border: 1px solid #f5c6cb;
}

.experience-form .btn {
  width: 100%;
  margin-top: var(--spacing-md);
}

.experience-form .btn:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}
</style>
