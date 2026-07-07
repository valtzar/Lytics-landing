<template>
  <transition name="toast-slide">
    <div v-if="isVisible" :class="['toast', `toast-${type}`]">
      <div class="toast-content">
        <span class="toast-icon">{{ icon }}</span>
        <span class="toast-message">{{ message }}</span>
      </div>
      <button class="toast-close" @click="close">✕</button>
    </div>
  </transition>
</template>

<script>
export default {
  name: 'Toast',
  props: {
    message: {
      type: String,
      required: true
    },
    type: {
      type: String,
      default: 'success',
      validator: (value) => ['success', 'error'].includes(value)
    },
    duration: {
      type: Number,
      default: 5000
    }
  },
  data() {
    return {
      isVisible: false,
      timeout: null
    }
  },
  computed: {
    icon() {
      return this.type === 'success' ? '✓' : '✕'
    }
  },
  watch: {
    message(newVal) {
      if (newVal) {
        this.show()
      }
    }
  },
  methods: {
    show() {
      this.isVisible = true
      
      if (this.timeout) {
        clearTimeout(this.timeout)
      }
      
      this.timeout = setTimeout(() => {
        this.close()
      }, this.duration)
    },
    close() {
      this.isVisible = false
      if (this.timeout) {
        clearTimeout(this.timeout)
      }
    }
  }
}
</script>

<style scoped>
.toast {
  position: fixed;
  bottom: 24px;
  right: 24px;
  padding: 16px 20px;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 12px;
  font-size: 14px;
  font-weight: 500;
  z-index: 10000;
  max-width: 400px;
  animation: slideIn 0.3s ease-out;
}

.toast-success {
  background-color: #d4edda;
  color: #155724;
  border: 1px solid #c3e6cb;
}

.toast-error {
  background-color: #f8d7da;
  color: #721c24;
  border: 1px solid #f5c6cb;
}

.toast-content {
  display: flex;
  align-items: center;
  gap: 12px;
}

.toast-icon {
  font-weight: bold;
  flex-shrink: 0;
}

.toast-message {
  line-height: 1.4;
}

.toast-close {
  background: none;
  border: none;
  color: inherit;
  cursor: pointer;
  padding: 0;
  font-size: 18px;
  flex-shrink: 0;
  transition: opacity 0.2s;
}

.toast-close:hover {
  opacity: 0.7;
}

@keyframes slideIn {
  from {
    transform: translateX(400px);
    opacity: 0;
  }
  to {
    transform: translateX(0);
    opacity: 1;
  }
}

.toast-slide-enter-active,
.toast-slide-leave-active {
  transition: all 0.3s ease;
}

.toast-slide-enter-from,
.toast-slide-leave-to {
  transform: translateX(400px);
  opacity: 0;
}

@media (max-width: 768px) {
  .toast {
    bottom: 16px;
    right: 16px;
    left: 16px;
    max-width: none;
  }
}
</style>
