<template>
  <div class="banner">
    <div class="banner-content">
      <h1 class="banner-title">Bienvenue dans notre boutique de bougies</h1>
      <p class="banner-subtitle">Des créations uniques pour illuminer vos moments.</p>
      <button class="banner-button">Explorer</button>
    </div>
  </div>
</template>

<script setup>
// Données ou props si nécessaire
</script>

<style scoped>
/* Mobile-first styles */
.banner {
  margin-top: 3rem;
  padding: 2rem;
  color: var(--text-color);
  text-align: center;
  background: url("@/assets/img/B3.jpg") no-repeat center;
  background-size: cover;
  height: auto; /* S'ajuste au contenu sur mobile */
}

.banner-content {
  max-width: 90%; /* Prend toute la largeur sur mobile */
  margin: 0 auto;
}

.banner-title {
  font-size: 1.8rem; /* Taille adaptée aux petits écrans */
  margin-bottom: 1rem;
  font-family: "Rubik Iso", cursive;
}

.banner-subtitle {
  font-size: 1rem;
  margin-bottom: 1.5rem;
  font-family: "Sour Gummy", sans-serif;
}

.banner-button {
  padding: 0.7rem 1.5rem;
  font-size: 1rem;
  background-color: var(--color-indigo);
  color: var(--text-color);
  border-radius: 5px;
  transition: background-color 0.3s ease, transform 0.3s ease;
}

.banner-button:hover {
  background-color: var(--color-lightgold);
  transform: scale(1.05);
}

/* Desktop styles */
@media (min-width: 768px) {
  .banner {
    margin-top: 5vh;
    height: 400px;
  }

  .banner-content {
    max-width: 800px;
  }

  .banner-title {
    font-size: 2.5rem;
  }

  .banner-subtitle {
    font-size: 1.2rem;
  }

  .banner-button {
    font-size: 1.2rem;
    padding: 0.8rem 2rem;
  }
}
</style>
