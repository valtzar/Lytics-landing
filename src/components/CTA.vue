<template>
  <section class="cta" id="cta">
    <div class="container">
      <div class="cta-content">
        <h2>Diseñado para tu Realidad</h2>
        <p>
          Un modelo predictivo que mide lo que realmente importa para tu negocio. 
          Acompañamiento + Software = People Analytics con rigor técnico y sensibilidad organizacional.
        </p>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'CTA'
}
</script>

<style scoped>
.cta {
  padding: var(--spacing-3xl) 0;
  background: linear-gradient(135deg, var(--color-primary) 0%, var(--color-primary-dark) 100%);
  color: var(--color-white);
}

.container {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 var(--spacing-md);
}

.cta-content {
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: var(--spacing-lg);
}

.cta-content h2 {
  font-size: var(--font-size-4xl);
  color: var(--color-white);
  margin: 0;
}

.cta-content > p {
  font-size: var(--font-size-lg);
  color: rgba(255, 255, 255, 0.9);
  max-width: 600px;
  margin: 0;
}

.cta-buttons {
  display: flex;
  gap: var(--spacing-md);
  margin: var(--spacing-lg) 0;
  justify-content: center;
}

.btn-large {
  padding: var(--spacing-md) var(--spacing-2xl);
  font-size: var(--font-size-lg);
}

.cta .btn-primary {
  background-color: var(--color-white);
  color: var(--color-primary);
}

.cta .btn-primary:hover {
  background-color: rgba(255, 255, 255, 0.9);
}

.cta .btn-secondary {
  background-color: transparent;
  color: var(--color-white);
  border-color: var(--color-white);
}

.cta .btn-secondary:hover {
  background-color: rgba(255, 255, 255, 0.1);
}

.cta-note {
  font-size: var(--font-size-sm);
  color: rgba(255, 255, 255, 0.8);
  margin: 0 !important;
}

@media (max-width: 768px) {
  .cta {
    padding: var(--spacing-2xl) 0;
  }

  .cta-content h2 {
    font-size: var(--font-size-3xl);
  }

  .cta-content > p {
    font-size: var(--font-size-base);
  }

  .cta-buttons {
    flex-direction: column;
    width: 100%;
  }

  .cta-buttons .btn {
    width: 100%;
  }
}
</style>
