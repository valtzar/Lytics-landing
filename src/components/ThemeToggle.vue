<template>
  <button 
    class="theme-toggle" 
    @click="toggleTheme"
    :aria-label="isDark ? 'Cambiar a modo claro' : 'Cambiar a modo oscuro'"
    :title="isDark ? 'Modo claro' : 'Modo oscuro'"
  >
    <svg v-if="!isDark" class="icon" viewBox="0 0 24 24" fill="currentColor">
      <!-- Moon icon for light mode -->
      <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/>
    </svg>
    <svg v-else class="icon" viewBox="0 0 24 24" fill="currentColor">
      <!-- Sun icon for dark mode -->
      <circle cx="12" cy="12" r="5"/>
      <line x1="12" y1="1" x2="12" y2="3" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
      <line x1="12" y1="21" x2="12" y2="23" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
      <line x1="4.22" y1="4.22" x2="5.64" y2="5.64" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
      <line x1="18.36" y1="18.36" x2="19.78" y2="19.78" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
      <line x1="1" y1="12" x2="3" y2="12" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
      <line x1="21" y1="12" x2="23" y2="12" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
      <line x1="4.22" y1="19.78" x2="5.64" y2="18.36" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
      <line x1="18.36" y1="5.64" x2="19.78" y2="4.22" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
    </svg>
  </button>
</template>

<script>
export default {
  name: 'ThemeToggle',
  data() {
    return {
      isDark: false
    }
  },
  mounted() {
    this.checkSystemPreference()
    window.matchMedia('(prefers-color-scheme: dark)').addEventListener('change', this.checkSystemPreference)
  },
  beforeUnmount() {
    window.matchMedia('(prefers-color-scheme: dark)').removeEventListener('change', this.checkSystemPreference)
  },
  methods: {
    checkSystemPreference() {
      const savedTheme = localStorage.getItem('theme')
      if (savedTheme) {
        this.isDark = savedTheme === 'dark'
        this.applyTheme(this.isDark)
      } else {
        this.isDark = window.matchMedia('(prefers-color-scheme: dark)').matches
        this.applyTheme(this.isDark)
      }
    },
    toggleTheme() {
      this.isDark = !this.isDark
      localStorage.setItem('theme', this.isDark ? 'dark' : 'light')
      this.applyTheme(this.isDark)
      this.$emit('theme-changed', this.isDark)
    },
    applyTheme(isDark) {
      if (isDark) {
        document.documentElement.style.colorScheme = 'dark'
        document.documentElement.setAttribute('data-theme', 'dark')
      } else {
        document.documentElement.style.colorScheme = 'light'
        document.documentElement.setAttribute('data-theme', 'light')
      }
    }
  }
}
</script>

<style scoped>
.theme-toggle {
  background: none;
  border: 2px solid var(--color-gray-300);
  border-radius: var(--border-radius-md);
  padding: var(--spacing-sm);
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--color-gray-700);
  transition: all var(--transition-fast);
  width: 40px;
  height: 40px;
}

.theme-toggle:hover {
  background-color: var(--color-gray-100);
  border-color: var(--color-gray-400);
  color: var(--color-black);
}

.icon {
  width: 20px;
  height: 20px;
  stroke-width: 2;
}
</style>
