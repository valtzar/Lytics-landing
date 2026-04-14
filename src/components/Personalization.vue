<template>
  <section class="personalization">
    <div class="container">
      <div class="personalization-header">
        <h2>¿Qué significa realmente "personalizado" en LYTICS?</h2>
      </div>

      <div class="personalization-grid">
        <div class="personalization-card">
          <div class="card-header">
            <div class="card-icon">✔</div>
            <h3>Competencias Diseñadas para tu Empresa</h3>
          </div>
          <div class="card-content">
            <p class="card-detail">No usamos diccionarios estándar. No aplicamos modelos genéricos.</p>
            <p>Cada organización define sus competencias estratégicas y LYTICS las integra en su matriz.</p>
            <p class="card-example">Ejemplos: Seguridad (minería, logística), Venta y servicio (retail, banca), Confidencialidad (salud, educación), Innovación, Liderazgo.</p>
          </div>
        </div>

        <div class="personalization-card">
          <div class="card-header">
            <div class="card-icon">✔</div>
            <h3>Ponderadores Ajustados a tu Cultura</h3>
          </div>
          <div class="card-content">
            <p>Cada una de las 7 variables se calibra según el contexto organizacional.</p>
            <p>El modelo refleja fielmente tu realidad interna y prioridades estratégicas.</p>
          </div>
        </div>

        <div class="personalization-card">
          <div class="card-header">
            <div class="card-icon">✔</div>
            <h3>Informes y Alarmas Adaptados a tu Estructura</h3>
          </div>
          <div class="card-content">
            <p>Las alarmas se ajustan a tus criterios de riesgo</p>
            <p>Los rankings se construyen según tus prioridades</p>
            <p>Las recomendaciones se alinean con tus políticas de DO</p>
          </div>
        </div>
      </div>

      <div class="personalization-quote">
        <p>"Las competencias se diseñan por grupos de trabajo que convivan diariamente."</p>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Personalization'
}
</script>

<style scoped>
.personalization {
  padding: var(--spacing-3xl) 0;
  background-color: var(--color-white);
}

.container {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 var(--spacing-md);
}

.personalization-header {
  text-align: center;
  margin-bottom: var(--spacing-3xl);
}

.personalization-header h2 {
  font-size: var(--font-size-4xl);
  color: var(--color-black);
  font-weight: var(--font-weight-bold);
}

.personalization-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: var(--spacing-xl);
  margin-bottom: var(--spacing-3xl);
}

.personalization-card {
  background-color: var(--color-gray-50);
  padding: var(--spacing-xl);
  border-radius: var(--border-radius-lg);
  border-left: 4px solid var(--color-primary);
}

.card-header {
  display: flex;
  align-items: flex-start;
  gap: var(--spacing-md);
  margin-bottom: var(--spacing-md);
}

.card-icon {
  font-size: var(--font-size-3xl);
  color: var(--color-primary);
  flex-shrink: 0;
}

.card-header h3 {
  font-size: var(--font-size-xl);
  color: var(--color-black);
  margin: 0;
  font-weight: var(--font-weight-bold);
}

.card-content {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-sm);
}

.card-content p {
  margin: 0;
  font-size: var(--font-size-base);
  color: var(--color-gray-700);
  line-height: var(--line-height-normal);
}

.card-detail {
  color: var(--color-primary);
  font-weight: var(--font-weight-bold);
}

.card-example {
  font-size: var(--font-size-sm);
  color: var(--color-gray-600);
  font-style: italic;
}

.personalization-quote {
  background: linear-gradient(135deg, var(--color-primary-light) 0%, rgba(0, 102, 204, 0.05) 100%);
  padding: var(--spacing-2xl);
  border-radius: var(--border-radius-lg);
  text-align: center;
  border-left: 4px solid var(--color-primary);
}

.personalization-quote p {
  font-size: var(--font-size-lg);
  color: var(--color-primary);
  margin: 0 0 var(--spacing-md) 0;
  font-weight: var(--font-weight-bold);
  line-height: var(--line-height-relaxed);
}

.personalization-quote p:last-child {
  margin-bottom: 0;
}

@media (max-width: 640px) {
  .personalization {
    padding: var(--spacing-2xl) 0;
  }

  .personalization-header h2 {
    font-size: var(--font-size-3xl);
  }

  .personalization-grid {
    gap: var(--spacing-lg);
  }

  .personalization-card {
    padding: var(--spacing-lg);
  }
}
</style>
