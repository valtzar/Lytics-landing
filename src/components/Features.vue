<template>
  <section class="features" id="features">
    <div class="container">
      <div class="features-header">
        <h2>Características Principales</h2>
        <p class="features-subtitle">
          Lytics combina tecnología avanzada con enfoque humano para transformar tu organización
        </p>
      </div>

      <div class="features-grid">
        <div class="feature-card">
          <div class="feature-icon">📊</div>
          <h3>Análisis Avanzado</h3>
          <p>
            Obtén insights profundos sobre el desarrollo de tu equipo con nuestras herramientas 
            de análisis de datos en tiempo real.
          </p>
        </div>

        <div class="feature-card">
          <div class="feature-icon">🎯</div>
          <h3>Objetivos Claros</h3>
          <p>
            Define y supervisa objetivos de desarrollo organizacional con métricas específicas 
            y seguimiento continuo.
          </p>
        </div>

        <div class="feature-card">
          <div class="feature-icon">👥</div>
          <h3>Gestión de Talento</h3>
          <p>
            Identifica talentos, planifica el desarrollo de carrera y optimiza el potencial 
            de tu equipo.
          </p>
        </div>

        <div class="feature-card">
          <div class="feature-icon">📈</div>
          <h3>Crecimiento Escalable</h3>
          <p>
            Diseña programas de desarrollo que crecen con tu organización, desde startups 
            hasta empresas grandes.
          </p>
        </div>

        <div class="feature-card">
          <div class="feature-icon">🔄</div>
          <h3>Integración Total</h3>
          <p>
            Se integra perfectamente con tus herramientas existentes para un flujo de trabajo 
            sin interrupciones.
          </p>
        </div>

        <div class="feature-card">
          <div class="feature-icon">🛡️</div>
          <h3>Seguridad Garantizada</h3>
          <p>
            Tus datos están protegidos con estándares de seguridad empresariales de nivel 
            internacional.
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Features'
}
</script>

<style scoped>
.features {
  padding: var(--spacing-3xl) 0;
  background-color: var(--color-gray-50);
}

.container {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 var(--spacing-md);
}

.features-header {
  text-align: center;
  margin-bottom: var(--spacing-3xl);
}

.features-header h2 {
  font-size: var(--font-size-4xl);
  margin-bottom: var(--spacing-md);
}

.features-subtitle {
  font-size: var(--font-size-lg);
  color: var(--color-gray-600);
  max-width: 600px;
  margin: 0 auto;
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: var(--spacing-xl);
}

.feature-card {
  background-color: var(--color-white);
  padding: var(--spacing-xl);
  border-radius: var(--border-radius-lg);
  box-shadow: var(--shadow-sm);
  transition: all var(--transition-base);
}

.feature-card:hover {
  box-shadow: var(--shadow-lg);
  transform: translateY(-5px);
}

.feature-icon {
  font-size: 48px;
  margin-bottom: var(--spacing-md);
}

.feature-card h3 {
  font-size: var(--font-size-2xl);
  margin-bottom: var(--spacing-md);
  color: var(--color-black);
}

.feature-card p {
  color: var(--color-gray-600);
  line-height: var(--line-height-relaxed);
  margin: 0;
}

@media (max-width: 768px) {
  .features {
    padding: var(--spacing-2xl) 0;
  }

  .features-header h2 {
    font-size: var(--font-size-3xl);
  }

  .features-grid {
    grid-template-columns: 1fr;
    gap: var(--spacing-lg);
  }

  .feature-card {
    padding: var(--spacing-lg);
  }

  .feature-icon {
    font-size: 40px;
  }

  .feature-card h3 {
    font-size: var(--font-size-xl);
  }
}
</style>
