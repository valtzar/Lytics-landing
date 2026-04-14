<template>
  <section class="features" id="features">
    <div class="container">
      <div class="features-header">
        <h2>El Modelo de 7 Variables</h2>
        <p class="features-subtitle">
          Validado empíricamente y patentado. Implementado en Zurich, Skechers y la Universidad de Chile.
        </p>
      </div>

      <div class="features-grid">
        <div class="feature-card">
          <div class="feature-icon">1️⃣</div>
          <h3>Autoevaluación</h3>
          <p>
            La perspectiva del colaborador sobre su desempeño y competencias.
          </p>
        </div>

        <div class="feature-card">
          <div class="feature-icon">2️⃣</div>
          <h3>Evaluación del Líder</h3>
          <p>
            Valoración de competencias desde la perspectiva de la gerencia.
          </p>
        </div>

        <div class="feature-card">
          <div class="feature-icon">3️⃣</div>
          <h3>Edad</h3>
          <p>
            Variable que influye en el comportamiento organizacional.
          </p>
        </div>

        <div class="feature-card">
          <div class="feature-icon">4️⃣</div>
          <h3>Compromiso</h3>
          <p>
            Nivel de compromiso e identificación con la empresa.
          </p>
        </div>

        <div class="feature-card">
          <div class="feature-icon">5️⃣</div>
          <h3>KPI Reales del Negocio</h3>
          <p>
            Indicadores concretos de desempeño del colaborador.
          </p>
        </div>

        <div class="feature-card">
          <div class="feature-icon">6️⃣</div>
          <h3>Antigüedad en el Cargo</h3>
          <p>
            El tiempo que lleva desempeñando la posición actual.
          </p>
        </div>

        <div class="feature-card">
          <div class="feature-icon">7️⃣</div>
          <h3>Ranking de Talentos</h3>
          <p>
            Medición integral de colaboradores.
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
