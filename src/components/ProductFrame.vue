<template>
  <div class="product-frame">
    <div class="image-container">
      <img class="product-image" :src="image" :alt="name" />
    </div>
    <div class="product-details">
      <h2 class="product-name">{{ name }}</h2>
      <p class="product-description">{{ description }}</p>
      <button class="product-button" @click="onActionClick">{{ buttonText }}</button>
    </div>
  </div>
</template>

<script setup>
import {defineProps, defineEmits} from "vue";

// Props pour personnaliser le produit
defineProps({
  image: {type: String, required: true},
  name: {type: String, required: true},
  description: {type: String, required: true},
  buttonText: {type: String, default: "Découvrir"},
});

// Événement d'action pour le bouton
const emit = defineEmits(["actionClick"]);

const onActionClick = () => {
  emit("actionClick");
};
</script>

<style scoped>
/* Conteneur principal */
.product-frame {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  padding: 1.5rem;
  border-radius: 12px;
  background: linear-gradient(to bottom, #ffffff, #f7f7f7);
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1), 0 1px 3px rgba(0, 0, 0, 0.06);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.product-frame:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.15), 0 4px 8px rgba(0, 0, 0, 0.1);
}

/* Image container avec effet subtil */
.image-container {
  width: 100%;
  max-width: 250px;
  height: 250px;
  overflow: hidden;
  border-radius: 12px;
  margin-bottom: 1rem;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.product-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.image-container:hover .product-image {
  transform: scale(1.1);
}

/* Détails du produit */
.product-details {
  color: var(--text-color);
  padding: 0 1rem;
}

/* Nom du produit */
.product-name {
  font-family: "Exo 2", cursive;
  font-size: 1.8rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
  color: var(--color-bordeaux);
}

/* Description */
.product-description {
  font-family: "Sour Gummy", sans-serif;
  font-size: 1rem;
  margin-bottom: 1.5rem;
  color: #666; /* Couleur douce pour le texte secondaire */
}

/* Bouton */
.product-button {
  padding: 0.8rem 1.8rem;
  font-family: "Sour Gummy", sans-serif;
  font-size: 1rem;
  background-color: var(--color-indigo);
  color: #fff;
  border: none;
  border-radius: 25px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: background-color 0.3s ease, box-shadow 0.3s ease, transform 0.3s ease;
}

.product-button:hover {
  background-color: var(--color-lightgold);
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2);
  transform: translateY(-2px);
}
</style>
