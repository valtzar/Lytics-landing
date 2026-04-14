<template>
  <section class="hero">
    <div class="container">
      <div class="hero-content">
        <div class="hero-text">
          <h1 class="hero-title">ERP para Desarrollo Organizacional</h1>
          <p class="hero-subtitle">Diseñado a la medida de tu organización</p>
          <p class="hero-description">
            LYTICS es el único software que mide tus competencias, en tu cultura y para tu negocio. 
            No usamos plantillas genéricas. Construimos un modelo predictivo único para cada empresa.
          </p>
          <div class="hero-buttons">
            <button class="btn btn-primary">Solicitar Demo</button>
            <button class="btn btn-secondary">Conocer Más</button>
          </div>
        </div>
        <div class="hero-image">
          <img src="@/assets/matriz talentos.svg" alt="Matriz de Talentos" class="hero-svg" />
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Hero'
}
</script>

<style scoped>
.hero {
  padding: var(--spacing-3xl) 0;
  background-color: var(--color-white);
}

.container {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 var(--spacing-md);
}

.hero-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--spacing-3xl);
  align-items: center;
}

.hero-text {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-lg);
}

.hero-title {
  font-size: var(--font-size-5xl);
  line-height: var(--line-height-tight);
  color: var(--color-black);
  font-weight: var(--font-weight-bold);
}

.hero-subtitle {
  font-size: var(--font-size-3xl);
  color: var(--color-primary);
  line-height: var(--line-height-relaxed);
  font-weight: var(--font-weight-bold);
}

.hero-description {
  font-size: var(--font-size-lg);
  color: var(--color-gray-600);
  line-height: var(--line-height-relaxed);
}

.hero-buttons {
  display: flex;
  gap: var(--spacing-md);
  margin-top: var(--spacing-md);
}

.hero-buttons .btn {
  padding: var(--spacing-md) var(--spacing-xl);
  font-size: var(--font-size-lg);
}

.hero-image {
  position: relative;
  height: 400px;
  border-radius: var(--border-radius-lg);
  display: flex;
  align-items: center;
  justify-content: center;
}

.hero-accent {
  max-width: 100%;
  max-height: 100%;
  width: auto;
  height: auto;
}

.hero-svg {
  max-width: 100%;
  max-height: 100%;
  width: auto;
  height: auto;
}

@keyframes float {
  0%, 100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-20px);
  }
}

@media (max-width: 1024px) {
  .hero-content {
    grid-template-columns: 1fr;
    gap: var(--spacing-2xl);
  }

  .hero-title {
    font-size: var(--font-size-4xl);
  }

  .hero-image {
    height: 300px;
  }

  .hero-accent {
    width: 200px;
    height: 200px;
  }
}

@media (max-width: 768px) {
  .hero {
    padding: var(--spacing-2xl) 0;
  }

  .hero-title {
    font-size: var(--font-size-3xl);
  }

  .hero-subtitle {
    font-size: var(--font-size-base);
  }

  .hero-buttons {
    flex-direction: column;
  }

  .hero-buttons .btn {
    width: 100%;
  }

  .hero-image {
    height: 250px;
  }

  .hero-accent {
    width: 150px;
    height: 150px;
  }
}
</style>
