<template>
  <section class="intelligent-alerts">
    <div class="container">
      <div class="alerts-header">
        <h2>Alarmas Inteligentes que se Ajustan a tu Cultura</h2>
        <p>LYTICS detecta riesgos reales dentro de tu organización, no de un modelo estándar.</p>
      </div>

      <div class="alerts-list">
        <div class="alert-item">
          <div class="alert-icon">⚠️</div>
          <div class="alert-content">
            <h3>Brechas entre Jefe y Colaborador</h3>
            <p>Si la diferencia es mayor a un 30% se genera una alarma de conflicto</p>
          </div>
        </div>

        <div class="alert-item">
          <div class="alert-icon">📊</div>
          <div class="alert-content">
            <h3>Talentos con Riesgo de Renuncia</h3>
            <p>Identifica colaboradores clave con probabilidad de abandono</p>
          </div>
        </div>

        <div class="alert-item">
          <div class="alert-icon">📚</div>
          <div class="alert-content">
            <h3>Falta de Competencias Críticas</h3>
            <p>Detecta brechas en habilidades estratégicas para el negocio</p>
          </div>
        </div>

        <div class="alert-item">
          <div class="alert-icon">👔</div>
          <div class="alert-content">
            <h3>Problemas de Liderazgo</h3>
            <p>Señala inconsistencias en el comportamiento de jefes</p>
          </div>
        </div>

        <div class="alert-item">
          <div class="alert-icon">💔</div>
          <div class="alert-content">
            <h3>Desmotivación</h3>
            <p>Detecta caídas en el nivel de compromiso del equipo</p>
          </div>
        </div>

        <div class="alert-item">
          <div class="alert-icon">🤝</div>
          <div class="alert-content">
            <h3>Equipos con Bajo Compromiso</h3>
            <p>Identifica grupos con problemas de cohesión y engagement</p>
          </div>
        </div>

        <div class="alert-item">
          <div class="alert-icon">🎓</div>
          <div class="alert-content">
            <h3>Necesidades de Capacitación Específicas</h3>
            <p>Sugiere programas de desarrollo personalizados por rol y competencia</p>
          </div>
        </div>
      </div>

      <div class="alerts-calibration">
        <p>✨ Todas estas alarmas se calibran según tus criterios internos y realidad organizacional</p>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'IntelligentAlerts'
}
</script>

<style scoped>
.intelligent-alerts {
  padding: var(--spacing-3xl) 0;
  background-color: var(--color-gray-50);
}

.container {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 var(--spacing-md);
}

.alerts-header {
  text-align: center;
  margin-bottom: var(--spacing-3xl);
}

.alerts-header h2 {
  font-size: var(--font-size-4xl);
  color: var(--color-black);
  font-weight: var(--font-weight-bold);
  margin-bottom: var(--spacing-md);
}

.alerts-header p {
  font-size: var(--font-size-lg);
  color: var(--color-gray-600);
}

.alerts-list {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: var(--spacing-xl);
  margin-bottom: var(--spacing-2xl);
}

.alert-item {
  display: flex;
  gap: var(--spacing-md);
  background-color: var(--color-white);
  padding: var(--spacing-xl);
  border-radius: var(--border-radius-lg);
  box-shadow: var(--shadow-sm);
  transition: all var(--transition-fast);
}

.alert-item:hover {
  box-shadow: var(--shadow-md);
  transform: translateY(-2px);
}

.alert-icon {
  font-size: var(--font-size-3xl);
  flex-shrink: 0;
}

.alert-content {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-sm);
}

.alert-content h3 {
  font-size: var(--font-size-lg);
  color: var(--color-black);
  margin: 0;
  font-weight: var(--font-weight-bold);
}

.alert-content p {
  margin: 0;
  font-size: var(--font-size-base);
  color: var(--color-gray-600);
  line-height: var(--line-height-normal);
}

.alerts-calibration {
  text-align: center;
  padding: var(--spacing-2xl);
  background: linear-gradient(135deg, rgba(77, 148, 255, 0.1) 0%, rgba(0, 102, 204, 0.05) 100%);
  border-radius: var(--border-radius-lg);
  border-left: 4px solid var(--color-primary);
}

.alerts-calibration p {
  font-size: var(--font-size-lg);
  color: var(--color-primary);
  font-weight: var(--font-weight-bold);
  margin: 0;
}

@media (max-width: 768px) {
  .intelligent-alerts {
    padding: var(--spacing-2xl) 0;
  }

  .alerts-header h2 {
    font-size: var(--font-size-3xl);
  }

  .alerts-list {
    grid-template-columns: 1fr;
  }
}
</style>
