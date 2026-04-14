<template>
  <section class="premium-service">
    <div class="container">
      <div class="service-header">
        <h2>Un Servicio Premium para Desarrollo Organizacional</h2>
        <p>LYTICS no es solo tecnología. Es una experiencia.</p>
      </div>

      <div class="service-content">
        <div class="service-items">
          <div class="service-item">
            <div class="item-number">1</div>
            <h3>Diseño de Competencias</h3>
            <p>Se diseñan competencias con la gerencia, adaptadas a tu realidad organizacional</p>
          </div>

          <div class="service-item">
            <div class="item-number">2</div>
            <h3>Calibración de Ponderadores</h3>
            <p>Se calibran ponderadores según tu cultura y estructura organizacional</p>
          </div>

          <div class="service-item">
            <div class="item-number">3</div>
            <h3>Ajuste de Alarmas y Umbrales</h3>
            <p>Se ajustan alarmas y umbrales según tus criterios internos de riesgo</p>
          </div>

          <div class="service-item">
            <div class="item-number">4</div>
            <h3>Interpretación de Resultados</h3>
            <p>Se interpretan resultados colaborativamente con tu equipo de DO</p>
          </div>

          <div class="service-item">
            <div class="item-number">5</div>
            <h3>Acciones Estratégicas</h3>
            <p>Se construyen acciones específicas y planes de intervención para tu realidad</p>
          </div>
        </div>

        <div class="service-highlight">
          <p class="highlight-title">People Analytics con:</p>
          <div class="highlight-features">
            <span class="feature">✓ Rigor Técnico</span>
            <span class="feature">✓ Sensibilidad Organizacional</span>
            <span class="feature">✓ Conocimiento del Negocio</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'PremiumService'
}
</script>

<style scoped>
.premium-service {
  padding: var(--spacing-3xl) 0;
  background: linear-gradient(135deg, var(--color-primary) 0%, var(--color-primary-dark) 100%);
  color: var(--color-white);
}

.container {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 var(--spacing-md);
}

.service-header {
  text-align: center;
  margin-bottom: var(--spacing-3xl);
}

.service-header h2 {
  font-size: var(--font-size-4xl);
  color: var(--color-white);
  font-weight: var(--font-weight-bold);
  margin-bottom: var(--spacing-md);
}

.service-header p {
  font-size: var(--font-size-xl);
  color: rgba(255, 255, 255, 0.9);
}

.service-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--spacing-3xl);
  align-items: center;
}

.service-items {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-lg);
}

.service-item {
  display: flex;
  gap: var(--spacing-lg);
  align-items: flex-start;
}

.item-number {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 50px;
  height: 50px;
  background-color: rgba(255, 255, 255, 0.2);
  border-radius: 50%;
  font-size: var(--font-size-2xl);
  font-weight: var(--font-weight-bold);
  color: var(--color-white);
  flex-shrink: 0;
}

.service-item h3 {
  font-size: var(--font-size-lg);
  color: var(--color-white);
  margin: 0 0 var(--spacing-sm) 0;
  font-weight: var(--font-weight-bold);
}

.service-item p {
  margin: 0;
  font-size: var(--font-size-base);
  color: rgba(255, 255, 255, 0.85);
  line-height: var(--line-height-normal);
}

.service-highlight {
  background-color: rgba(255, 255, 255, 0.1);
  padding: var(--spacing-2xl);
  border-radius: var(--border-radius-lg);
  border: 2px solid rgba(255, 255, 255, 0.2);
  text-align: center;
}

.highlight-title {
  font-size: var(--font-size-xl);
  color: var(--color-white);
  font-weight: var(--font-weight-bold);
  display: block;
  margin-bottom: var(--spacing-lg);
}

.highlight-features {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-md);
}

.feature {
  font-size: var(--font-size-lg);
  color: rgba(255, 255, 255, 0.95);
  font-weight: var(--font-weight-bold);
}

@media (max-width: 768px) {
  .premium-service {
    padding: var(--spacing-2xl) 0;
  }

  .service-header h2 {
    font-size: var(--font-size-3xl);
  }

  .service-content {
    grid-template-columns: 1fr;
  }

  .service-items {
    gap: var(--spacing-md);
  }
}
</style>
