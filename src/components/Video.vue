<template>
  <section class="video-section" id="video">
    <div class="container">
      <div class="video-header">
        <h2>Bienvenido a Lytics</h2>
        <p>Descubre cómo Lytics transforma el desarrollo organizacional</p>
        
        <div class="logos-container">
          <img src="@/assets/Logo LYTICS MEX.png" alt="Lytics México" class="logo-image" />
          <img src="@/assets/Logo LYTICS CHI.png" alt="Lytics Chile" class="logo-image" />
          <img src="@/assets/Logo LYTICS ESP.png" alt="Lytics España" class="logo-image" />
        </div>
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
  padding-top: var(--spacing-3xl);
  padding-bottom: var(--spacing-3xl);
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
  color: var(--color-gray-700);
}

.video-header p {
  font-size: var(--font-size-lg);
  color: var(--color-gray-600);
  margin: 0 0 var(--spacing-2xl) 0;
}

.logos-container {
  display: flex;
  gap: var(--spacing-xl);
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  margin-top: var(--spacing-2xl);
}

.logo-image {
  max-width: 250px;
  height: auto;
  object-fit: contain;
  filter: drop-shadow(0 2px 8px rgba(0, 0, 0, 0.1));
  transition: transform var(--transition-fast);
}

.logo-image:hover {
  transform: scale(1.05);
}

.video-container {
  position: relative;
  width: 100vw;
  left: 50%;
  right: 50%;
  margin-left: -50vw;
  margin-right: -50vw;
  padding-bottom: 36.25%;
  height: 0;
  overflow: hidden;
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

  .logo-image {
    max-width: 150px;
  }

  .video-container {
    border-radius: var(--border-radius-md);
  }
}
</style>
