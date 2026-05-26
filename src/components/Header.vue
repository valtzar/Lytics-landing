<template>
  <header class="header">
    <div class="container">
      <div class="header-content">
        <a href="#video" class="logo-link">
          <Logo height="100px" />
        </a>
        <nav class="nav">
          <a href="#features" class="nav-link">Características</a>
          <a href="#video" class="nav-link">Demostración</a>
          <a href="#contact" class="nav-link">Contacto</a>
        </nav>
        <div class="header-actions">
          <ThemeToggle />
          <a href="#contact" class="btn btn-primary nav-cta">Comenzar Ahora</a>
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
}

.nav-link:hover {
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

@media (max-width: 768px) {
  .header-content {
    flex-direction: column;
    gap: var(--spacing-md);
    padding: var(--spacing-md) 0;
  }

  .nav {
    flex-direction: column;
    width: 100%;
    gap: var(--spacing-md);
    align-items: center;
  }

  .nav-link {
    font-size: var(--font-size-sm);
  }

  .nav-cta {
    width: 100%;
  }
}
</style>
