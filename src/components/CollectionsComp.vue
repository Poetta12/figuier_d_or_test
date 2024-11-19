<template>
  <section class="collections">
    <h2 class="section-title">Découvrez nos collections</h2>
    <div class="collection-list">
      <div class="collection-item" v-for="collection in collections" :key="collection.id">
        <div
          class="collection-image"
          :style="{ backgroundImage: `url(${collection.image})` }"
        ></div>
        <div class="collection-content">
          <h3 class="collection-title">{{ collection.title }}</h3>
          <p class="collection-description">{{ collection.description }}</p>

        </div>
        <button class="explore-button">Explorer la boutique</button>
      </div>
    </div>
  </section>
</template>


<script setup>
const collections = [
  {
    id: 1,
    title: "Bougies moulées",
    description: "Des formes élégantes et uniques.",
    image: "/img/moule-bougie-originale.webp",
  },
  {
    id: 2,
    title: "Bougies parfumées",
    description: "Des belles senteurs envoûtantes.",
    image: "/img/bougie-parfumée.png",
  },
  {
    id: 3,
    title: "Bougies Fondantes",
    description: "Des parfums pour chaque humeur.",
    image: "/img/bougie-fondant.webp",
  },
  {
    id: 4,
    title: "Bougies de massage",
    description: "Relaxez-vous tranquillement avec style.",
    image: "/img/Massage-bougie.jpeg",
  },
];
</script>


<style scoped>
/* Section générale */
button:hover,
a:hover {
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
  color: var(--color-lightgold);
  margin-bottom: 1.5rem;
  text-shadow: 2px 2px var(--color-black);
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
  border-radius: 15px;
  overflow: hidden;
  width: 90%;
  max-width: 300px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  text-align: center;
  box-shadow: 0 4px 6px var(--color-darkgold);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.collection-item:hover {
  transform: translateY(-5px);
  box-shadow: 0 6px 10px var(--color-lightgold);
}

/* Image d'arrière-plan */
.collection-image {
  width: 100%;
  height: 200px;
  background-size: cover;
  background-position: center;
  border-radius: 15px 15px 0 0;
}

/* Contenu de la collection */
.collection-content {
  display: flex;
  flex-direction: column;
  background-color: var(--color-indigo);
  color: var(--text-color);
}

.collection-content:last-child{
  justify-self: flex-end;
}

.collection-title {
  font-family: "Rubik Iso", cursive;
  font-size: 1.5rem;
  margin-bottom: 0.5rem;
  color: var(--color-lightgold);
  text-shadow: 0 2px 4px var(--color-darkgold);
}

.collection-description {
  font-family: "Sour Gummy", sans-serif;
  font-size: 1rem;
  margin-bottom: 1rem;
}

/* Bouton Explorer */
.explore-button {
  background-color: var(--color-lightgold);
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
  color: var(--color-lightgold);
  transform: scale(1.1);
}

/* Grille pour tablettes et desktops */
@media (min-width: 768px) {
  .collection-list {
    grid-template-columns: repeat(2, 1fr);
    gap: 2rem;
  }
}

@media (min-width: 1024px) {
  .collections {
    margin-top: 2rem;
    background-color: var(--color-bg-white-tranp);
    border-radius: 20px 5px 20px 5px;
  }

  .collection-list {
    grid-template-columns: repeat(4, 1fr);
    gap: 1rem;
  }

  .collection-item {
    width: 100%;
  }
  .collection-content{
    padding: 0 10px;
  }
}
</style>
