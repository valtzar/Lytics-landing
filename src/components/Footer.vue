<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
      </div>

      <div class="footer-bottom">
        <p>&copy; 2026 Lytics. Todos los derechos reservados.</p>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Footer'
}
</script>

<style scoped>
.footer {
  background-color: #0F1419;
  color: #FFFFFF;
  padding: var(--spacing-3xl) 0 var(--spacing-xl);
}

.container {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 var(--spacing-md);
}

.footer-content {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: var(--spacing-2xl);
  margin-bottom: var(--spacing-2xl);
  padding-bottom: var(--spacing-2xl);
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.footer-section h4,
.footer-section h5 {
  color: #FFFFFF;
  margin-bottom: var(--spacing-md);
}

.footer-section p {
  color: rgba(255, 255, 255, 0.8);
  font-size: var(--font-size-sm);
  line-height: var(--line-height-relaxed);
  margin-bottom: var(--spacing-md);
}

.footer-section ul {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: var(--spacing-sm);
}

.footer-section a {
  color: rgba(255, 255, 255, 0.8);
  font-size: var(--font-size-sm);
  transition: color var(--transition-fast);
}

.footer-section a:hover {
  color: #FFFFFF;
}

.social-links {
  display: flex;
  gap: var(--spacing-md);
  margin-top: var(--spacing-md);
}

.social-links a {
  font-size: var(--font-size-sm);
}

.footer-bottom {
  text-align: center;
  color: rgba(255, 255, 255, 0.6);
  font-size: var(--font-size-sm);
}

@media (max-width: 768px) {
  .footer {
    padding: var(--spacing-2xl) 0 var(--spacing-lg);
  }

  .footer-content {
    grid-template-columns: 1fr;
    gap: var(--spacing-lg);
  }

  .footer-section {
    text-align: center;
  }

  .footer-section ul {
    align-items: center;
  }

  .social-links {
    justify-content: center;
  }
}
</style>
