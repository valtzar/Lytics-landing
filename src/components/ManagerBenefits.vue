<template>
  <section class="manager-benefits">
    <div class="container">
      <div class="benefits-header">
        <h2>🚀 ¿Qué Obtiene un Gerente de DO con un Sistema 100% Personalizado?</h2>
      </div>

      <div class="benefits-grid">
        <div class="benefit-card">
          <div class="benefit-icon">🎯</div>
          <h3>Modelo Predictivo Alineado</h3>
          <p>Un coeficiente de actividad humana único alineado a tu estrategia y realidad</p>
        </div>

        <div class="benefit-card">
          <div class="benefit-icon">🗺️</div>
          <h3>Mapa Real del Talento</h3>
          <p>Diagnóstico completo según competencias propias de tu organización</p>
        </div>

        <div class="benefit-card">
          <div class="benefit-icon">👥</div>
          <h3>Diagnóstico de Liderazgo</h3>
          <p>Evaluación adaptada a tu cultura y definiciones de liderazgo efectivo</p>
        </div>

        <div class="benefit-card">
          <div class="benefit-icon">⚡</div>
          <h3>Alertas Tempranas</h3>
          <p>Sistema de alarmas calibrado según tus criterios internos de riesgo</p>
        </div>

        <div class="benefit-card">
          <div class="benefit-icon">📊</div>
          <h3>Ranking Objetivo</h3>
          <p>Clasificación de colaboradores basada en variables definidas por la empresa</p>
        </div>

        <div class="benefit-card">
          <div class="benefit-icon">⏱️</div>
          <h3>Ahorro de Tiempo</h3>
          <p>90% menos tiempo en procesos de evaluación y análisis manual</p>
        </div>

        <div class="benefit-card">
          <div class="benefit-icon">💡</div>
          <h3>Insumo Estratégico</h3>
          <p>Datos sólidos para decisiones de alto nivel en DO y gestión de talento</p>
        </div>

        <div class="benefit-card">
          <div class="benefit-icon">🔄</div>
          <h3>Continuo Mejoramiento</h3>
          <p>Follow-up y ajustes constantes según evolución de tu organización</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ManagerBenefits'
}
</script>

<style scoped>
.manager-benefits {
  padding: var(--spacing-3xl) 0;
  background-color: var(--color-white);
}

.container {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 var(--spacing-md);
}

.benefits-header {
  text-align: center;
  margin-bottom: var(--spacing-3xl);
}

.benefits-header h2 {
  font-size: var(--font-size-4xl);
  color: var(--color-black);
  font-weight: var(--font-weight-bold);
  line-height: var(--line-height-tight);
}

.benefits-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: var(--spacing-xl);
}

.benefit-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  padding: var(--spacing-xl);
  background-color: var(--color-gray-50);
  border-radius: var(--border-radius-lg);
  border-top: 4px solid var(--color-primary);
  transition: all var(--transition-fast);
}

.benefit-card:hover {
  box-shadow: var(--shadow-lg);
  transform: translateY(-4px);
  background-color: var(--color-white);
}

.benefit-icon {
  font-size: var(--font-size-4xl);
  margin-bottom: var(--spacing-md);
}

.benefit-card h3 {
  font-size: var(--font-size-lg);
  color: var(--color-black);
  margin: 0 0 var(--spacing-sm) 0;
  font-weight: var(--font-weight-bold);
}

.benefit-card p {
  margin: 0;
  font-size: var(--font-size-base);
  color: var(--color-gray-600);
  line-height: var(--line-height-normal);
}

@media (max-width: 768px) {
  .manager-benefits {
    padding: var(--spacing-2xl) 0;
  }

  .benefits-header h2 {
    font-size: var(--font-size-3xl);
  }

  .benefits-grid {
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: var(--spacing-lg);
  }

  .benefit-card {
    padding: var(--spacing-lg);
  }
}
</style>
