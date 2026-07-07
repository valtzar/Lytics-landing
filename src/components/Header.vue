<template>
  <header class="header">
    <div class="container">
      <div class="header-content">
        <a href="#video" class="logo-link">
          <Logo height="100px" />
        </a>
        <button class="menu-toggle" @click="toggleMobileMenu" :class="{ open: isMobileMenuOpen }">
          <span class="menu-arrow">▼</span>
        </button>
        <nav class="nav" :class="{ active: isMobileMenuOpen }">
          <div class="dropdown-container">
            <button class="nav-link dropdown-toggle" @click="toggleDropdown">
              Certificaciones
              <span class="dropdown-arrow" :class="{ open: isDropdownOpen }">▼</span>
            </button>
            <div class="dropdown-menu" v-show="isDropdownOpen">
              <a href="#" class="dropdown-item" @click="closeMobileMenu">Desarrollo Organizacional</a>
              <a href="#" class="dropdown-item" @click="closeMobileMenu">IA para gestionar personas</a>
              <a href="#" class="dropdown-item" @click="closeMobileMenu">Selección por competencias básico y avanzado</a>
              <a href="#" class="dropdown-item" @click="closeMobileMenu">Plataforma Lytics</a>
              <a href="#" class="dropdown-item" @click="closeMobileMenu">Coaching metodología Rapport</a>
              <a href="#" class="dropdown-item" @click="closeMobileMenu">Diseño Evaluación del Desempeño</a>
              <a href="#" class="dropdown-item" @click="closeMobileMenu">Diseño perfiles de Cargo con IA</a>
              <a href="#" class="dropdown-item" @click="closeMobileMenu">Consultoría en Gestión de personas</a>
            </div>
          </div>
        </nav>
        <div class="header-actions" :class="{ active: isMobileMenuOpen }">
          <ThemeToggle />
          <a href="https://seleccion.lytics.cl/" class="btn btn-primary nav-cta" target="_blank" rel="noopener noreferrer" @click="closeMobileMenu">Comenzar Ahora</a>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
import Logo from './Logo.vue'
import ThemeToggle from './ThemeToggle.vue'

export default {
  name: 'Header',
  components: {
    Logo,
    ThemeToggle
  },
  data() {
    return {
      isDropdownOpen: false,
      isMobileMenuOpen: false
    }
  },
  methods: {
    toggleDropdown() {
      this.isDropdownOpen = !this.isDropdownOpen
    },
    closeDropdown() {
      this.isDropdownOpen = false
    },
    toggleMobileMenu() {
      this.isMobileMenuOpen = !this.isMobileMenuOpen
    },
    closeMobileMenu() {
      this.isMobileMenuOpen = false
      this.isDropdownOpen = false
    }
  },
  mounted() {
    document.addEventListener('click', (e) => {
      if (!this.$el.querySelector('.dropdown-container').contains(e.target)) {
        this.closeDropdown()
      }
    })
  }
}
</script>

<style scoped>
.header {
  background-color: var(--color-white);
  border-bottom: 1px solid var(--color-gray-100);
  position: sticky;
  top: 0;
  z-index: 100;
  box-shadow: var(--shadow-sm);
}

.container {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 var(--spacing-md);
}

.logo-link {
  display: flex;
  align-items: center;
  text-decoration: none;
  cursor: pointer;
  transition: opacity var(--transition-fast);
  flex-shrink: 0;
}

.logo-link:hover {
  opacity: 0.8;
}

.header-content {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: var(--spacing-md) 0;
  gap: var(--spacing-xl);
}

.nav {
  display: flex;
  align-items: center;
  gap: var(--spacing-xl);
  flex: 1;
  justify-content: center;
}

.nav-link {
  font-weight: var(--font-weight-bold);
  color: var(--color-gray-700);
  transition: color var(--transition-fast);
  background: none;
  border: none;
  cursor: pointer;
  padding: 0;
  font-size: inherit;
  font-family: inherit;
}

.nav-link:hover {
  color: var(--color-primary);
}

.dropdown-container {
  position: relative;
}

.dropdown-toggle {
  display: flex;
  align-items: center;
  gap: var(--spacing-xs);
}

.dropdown-arrow {
  font-size: 0.7em;
  transition: transform var(--transition-fast);
}

.dropdown-arrow.open {
  transform: rotate(180deg);
}

.dropdown-menu {
  position: absolute;
  top: 100%;
  left: 0;
  background-color: var(--color-white);
  border: 1px solid var(--color-gray-100);
  border-radius: var(--border-radius-md);
  box-shadow: var(--shadow-md);
  min-width: 280px;
  margin-top: var(--spacing-sm);
  z-index: 1000;
}

.dropdown-item {
  display: block;
  padding: var(--spacing-sm) var(--spacing-md);
  color: var(--color-gray-700);
  text-decoration: none;
  transition: all var(--transition-fast);
  font-weight: var(--font-weight-normal);
  font-size: var(--font-size-sm);
}

.dropdown-item:first-child {
  border-radius: var(--border-radius-md) var(--border-radius-md) 0 0;
}

.dropdown-item:last-child {
  border-radius: 0 0 var(--border-radius-md) var(--border-radius-md);
}

.dropdown-item:hover {
  background-color: var(--color-gray-50);
  color: var(--color-primary);
}

.header-actions {
  display: flex;
  align-items: center;
  gap: var(--spacing-md);
  flex-shrink: 0;
  justify-content: flex-end;
}

.nav-cta {
  flex-shrink: 0;
}

.nav-cta:hover {
  color: var(--color-white);
}

.menu-toggle {
  display: none;
  background: none;
  border: none;
  cursor: pointer;
  padding: var(--spacing-sm);
  width: 48px;
  height: 48px;
  align-items: center;
  justify-content: center;
}

.menu-arrow {
  font-size: var(--font-size-2xl);
  color: var(--color-gray-700);
  transition: transform var(--transition-fast);
  display: inline-block;
}

.menu-toggle.open .menu-arrow {
  transform: rotate(180deg);
}

@media (max-width: 768px) {
  .header-content {
    display: grid;
    grid-template-columns: 1fr auto;
    align-items: center;
    padding: var(--spacing-md) 0;
    gap: var(--spacing-md);
  }

  .menu-toggle {
    display: flex;
    grid-column: 2;
    grid-row: 1;
  }

  .nav {
    grid-column: 1 / -1;
    flex-direction: column;
    width: 100%;
    gap: var(--spacing-md);
    align-items: flex-start;
    max-height: 0;
    overflow: hidden;
    transition: max-height var(--transition-fast);
  }

  .nav.active {
    max-height: 500px;
    padding: var(--spacing-md) 0;
    border-top: 1px solid var(--color-gray-100);
    border-bottom: 1px solid var(--color-gray-100);
  }

  .nav-link {
    font-size: var(--font-size-sm);
  }

  .header-actions {
    display: none;
    grid-column: 1 / -1;
    flex-direction: column;
    gap: var(--spacing-md);
    width: 100%;
  }

  .header-actions.active {
    display: flex;
  }

  .nav-cta {
    width: 100%;
  }

  .dropdown-menu {
    position: static;
    min-width: 100%;
    box-shadow: none;
    border: none;
    border-radius: 0;
    background-color: var(--color-gray-50);
    margin: 0;
    margin-top: var(--spacing-sm);
  }

  .dropdown-item {
    border-radius: 0;
  }

  .dropdown-item:first-child {
    border-radius: 0;
  }

  .dropdown-item:last-child {
    border-radius: 0;
  }
}
</style>
