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
  { id: 3, title: "Bougies Fondants", description: "Des parfums pour chaque humeur." },
  { id: 4, title: "Bougies de massage", description: "Relaxez-vous avec style." },
];
</script>

<style scoped>
/* Section générale */
button:hover, a:hover {
  cursor: none;
}

.collections {
  padding: 2rem 1rem;
  background-color: var(--bg-color);
  color: var(--text-color);
  text-align: center;
}

.section-title {
  font-family: "Rubik Iso", cursive;
  font-size: 2rem;
<<<<<<< HEAD
  color: var(--color-light-gold); /* Light gold */
=======
  color: var(--color-lightgold);
>>>>>>> a035d82bd60eec956ffa02b9261713ff7d8be08f
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
  box-shadow: 0 4px 6px var(--color-darkgold);
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
  box-shadow: 0 6px 10px var(--color-lightgold);
}

/* Titre de collection */
.collection-title {
  font-family: "Rubik Iso", cursive;
  font-size: 1.5rem;
  margin-bottom: 0.5rem;
<<<<<<< HEAD
  color: var(--color-light-gold); /* Light gold */
=======
  color: var(--color-lightgold);
  text-shadow: 0 2px 4px var(--color-darkgold);
>>>>>>> a035d82bd60eec956ffa02b9261713ff7d8be08f
}

.collection-description {
  font-family: "Sour Gummy", sans-serif;
  font-size: 1rem;
  margin-bottom: 1rem;
}

/* Bouton Explorer */
.explore-button {
<<<<<<< HEAD
  background-color: var(--color-dark-gold); /* Dark gold */
=======
  background-color: var(--color-lightgold);
>>>>>>> a035d82bd60eec956ffa02b9261713ff7d8be08f
  color: var(--color-bordeaux);
  border: none;
  border-radius: 5px;
  padding: 0.7rem 1rem;
  cursor: pointer;
  font-family: "Sour Gummy", sans-serif;
  font-size: 1rem;
  transition: background-color 0.3s ease, color 0.3s ease, transform 0.3s ease;
}

.explore-button:hover {
  background-color: var(--color-bordeaux);
<<<<<<< HEAD
  color: var(--color-light-gold); /* Light gold */
=======
  color: var(--color-lightgold);
  transform: scale(1.1);
>>>>>>> a035d82bd60eec956ffa02b9261713ff7d8be08f
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
