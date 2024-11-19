<template>
  <div class="figue-container">
    <div class="figue">
      <!-- Texture et détails (si nécessaire, ajouter des décorations ici) -->
      <div class="shadow"></div>
    </div>
  </div>
</template>

<script setup>
</script>

<style scoped>
/* Conteneur principal */
.figue-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #f9f9f9;
}

/* Figue réaliste */
.figue {
  position: relative;
  width: 150px; /* Taille de la figue */
  height: 200px;
  background: url('@/assets/figue.png') no-repeat center center;
  background-size: cover;
  animation: float 3s ease-in-out infinite;
}

/* Ombre douce sous la figue */
.shadow {
  position: absolute;
  bottom: -20px;
  left: 50%;
  transform: translateX(-50%);
  width: 100px;
  height: 30px;
  background: radial-gradient(circle, rgba(0, 0, 0, 0.2), transparent);
  border-radius: 50%;
  z-index: -1;
}

/* Animation pour un effet de flottement */
@keyframes float {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
}
</style>
