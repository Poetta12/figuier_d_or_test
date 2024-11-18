<template>
  <section class="collections">
    <h2>Découvrez nos collections</h2>
    <div class="collection-list">
      <div class="collection-item" v-for="collection in collections" :key="collection.id">
        <h3>{{ collection.title }}</h3>
        <p>{{ collection.description }}</p>
        <button>Explorer la boutique</button>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "CollectionsComp",
  data() {
    return {
      collections: [
        { id: 1, title: "Bougies moulées", description: "Des formes élégantes et uniques." },
        { id: 2, title: "Bougies parfumées", description: "Des senteurs envoûtantes." },
        { id: 3, title: "Fondants", description: "Des parfums pour chaque humeur." },
        { id: 4, title: "Bougies de massage", description: "Relaxez-vous avec style." },
      ],
    };
  },
};
</script>

<style scoped>
.collections {
  text-align: center;
  margin: 2rem 0;
  color: var(--color-gold);
}

.collection-list {
  display: flex;
  justify-content: space-evenly;
  flex-wrap: wrap;
}

.collection-item {
  background-color: var(--color-indigo);
  color: var(--text-color);
  padding: 1rem;
  border-radius: 10px;
  width: 24%;
  height: 150px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}

.collection-item h3 {
  font-family: "Nexa Script", cursive;
}

button {
  background-color: var(--color-bordeaux);
  color: var(--color-gold);
  border: none;
  padding: 0.5rem 1rem;
  cursor: pointer;
  border-radius: 5px;
}

button:hover {
  background-color: var(--color-gold);
  color: var(--color-bordeaux);
}
</style>
