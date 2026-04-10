<template>
  <section class="video-section" id="video">
    <div class="container">
      <div class="video-header">
        <h2>Ve Lytics en Acción</h2>
        <p>Descubre cómo Lytics transforma el desarrollo organizacional en tiempo real</p>
      </div>

      <div class="video-container">
        <video 
          class="video-element" 
          autoplay 
          muted 
          loop 
          playsinline
        >
          <source src="@/assets/mixkit-corporate-and-business-buildings-in-the-city-4170-hd-ready.mp4" type="video/mp4">
          Tu navegador no soporta el elemento de video.
        </video>
        <div class="video-overlay"></div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Video'
}
</script>

<style scoped>
.video-section {
  padding: var(--spacing-3xl) 0;
  background-color: var(--color-white);
}

.container {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 var(--spacing-md);
}

.video-header {
  text-align: center;
  margin-bottom: var(--spacing-2xl);
}

.video-header h2 {
  font-size: var(--font-size-4xl);
  margin-bottom: var(--spacing-md);
}

.video-header p {
  font-size: var(--font-size-lg);
  color: var(--color-gray-600);
  margin: 0;
}

.video-container {
  position: relative;
  width: 100%;
  padding-bottom: 56.25%;
  height: 0;
  overflow: hidden;
  border-radius: var(--border-radius-lg);
  background-color: var(--color-gray-100);
  box-shadow: var(--shadow-lg);
}

.video-element {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.video-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(to bottom, rgba(0, 0, 0, 0.1), transparent, rgba(0, 0, 0, 0.05));
  pointer-events: none;
}

@media (max-width: 768px) {
  .video-section {
    padding: var(--spacing-2xl) 0;
  }

  .video-header h2 {
    font-size: var(--font-size-3xl);
  }

  .video-header p {
    font-size: var(--font-size-base);
  }

  .video-container {
    border-radius: var(--border-radius-md);
  }
}
</style>
