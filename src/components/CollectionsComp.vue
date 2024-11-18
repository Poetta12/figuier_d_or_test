<template>
  <section class="collections">
    <h2 class="section-title">Découvrez nos collections</h2>
    <div class="collection-list">
      <div class="collection-item" v-for="collection in collections" :key="collection.id">
        <h3 class="collection-title">{{ collection.title }}</h3>
        <p class="collection-description">{{ collection.description }}</p>
        <button class="explore-button">Explorer la boutique</button>
      </div>
    </div>
  </section>
</template>

<script setup>
const collections = [
  { id: 1, title: "Bougies moulées", description: "Des formes élégantes et uniques." },
  { id: 2, title: "Bougies parfumées", description: "Des senteurs envoûtantes." },
  { id: 3, title: "Fondants", description: "Des parfums pour chaque humeur." },
  { id: 4, title: "Bougies de massage", description: "Relaxez-vous avec style." },
];
</script>

<style scoped>
/* Section générale */
button:hover, a:hover{
  cursor: none;
}

.collections {
  padding: 2rem 1rem;
  background-color: var(--bg-color);
  color: var(--text-color);
  text-align: center;
}

.section-title {
  font-family: "Nexa Script", cursive;
  font-size: 2rem;
  color: var(--color-gold);
  margin-bottom: 1.5rem;
}

/* Liste des collections */
.collection-list {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1.5rem;
  justify-items: center;
}

/* Éléments des collections */
.collection-item {
  background-color: var(--color-indigo);
  color: var(--text-color);
  padding: 1.5rem;
  border-radius: 15px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  width: 90%;
  max-width: 300px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  text-align: center;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.collection-item:hover {
  transform: translateY(-5px);
  box-shadow: 0 6px 10px rgba(0, 0, 0, 0.2);
}

.collection-title {
  font-family: "Nexa Script", cursive;
  font-size: 1.5rem;
  margin-bottom: 0.5rem;
}

.collection-description {
  font-family: "Tan Tangkiewood", sans-serif;
  font-size: 1rem;
  margin-bottom: 1rem;
}

/* Bouton Explorer */
.explore-button {
  background-color: var(--color-gold);
  color: var(--color-bordeaux);
  border: none;
  border-radius: 5px;
  padding: 0.7rem 1rem;
  cursor: pointer;
  font-family: "Tan Tangkiewood", sans-serif;
  font-size: 1rem;
  transition: background-color 0.3s ease, color 0.3s ease;
}

.explore-button:hover {
  background-color: var(--color-bordeaux);
  color: var(--color-gold);
}

/* Grille pour tablettes et desktops */
@media (min-width: 768px) {
  .collection-list {
    grid-template-columns: repeat(2, 1fr);
    gap: 2rem;
  }
}

@media (min-width: 1024px) {
  .collection-list {
    grid-template-columns: repeat(4, 1fr);
    gap: 2rem;
  }

  .collection-item {
    width: 100%;
  }
}
</style>
