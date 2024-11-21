<template>
  <div class="product-frame">
    <div class="image-container">
      <img class="product-image" :src="image" :alt="name" />
    </div>
    <div class="product-details">
      <h2 class="product-name">{{ name }}</h2>
      <p class="product-description">{{ description }}</p>
    </div>
    <button class="product-button" @click="onActionClick">{{ buttonText }}</button>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from "vue";

// Props pour personnaliser le produit
defineProps({
  image: { type: String, required: true },
  name: { type: String, required: true },
  description: { type: String, required: true },
  buttonText: { type: String, default: "Découvrir" },
});

// Événement d'action pour le bouton
const emit = defineEmits(["actionClick"]);

const onActionClick = () => {
  emit("actionClick");
};
</script>

<style scoped>
/* Base styles: mobile-first */

/* Conteneur principal */
.product-frame {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  text-align: center;
  padding: 1rem;
  border-radius: 10px;
  background: #ffffff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.product-frame:hover {
  transform: translateY(-3px);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
}

/* Conteneur de l'image */
.image-container {
  width: 100%;
  max-width: 200px;
  height: 200px;
  overflow: hidden;
  border-radius: 8px;
  margin-bottom: 1rem;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
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
  padding: 0 0.5rem;
  color: var(--text-color);
}

/* Nom du produit */
.product-name {
  font-size: 3rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
  color: var(--color-bordeaux);
}

/* Description */
.product-description {
  font-size: 0.9rem;
  margin-bottom: 1rem;
  color: #666;
}

/* Bouton */
.product-button {
  padding: 0.5rem 1rem;
  font-size: 0.9rem;
  background-color: var(--color-indigo);
  color: #fff;
  border: none;
  border-radius: 20px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  transition: background-color 0.3s ease, transform 0.3s ease;
}

.product-button:hover {
  background-color: var(--color-lightgold);
  transform: translateY(-2px);
}

/* Styles supplémentaires pour tablettes et desktops */

/* Tablettes (min-width: 768px) */
@media (min-width: 768px) {
  .product-frame {
    padding: 1.5rem;
    border-radius: 12px;
  }

  .image-container {
    max-width: 250px;
    height: 250px;
    margin-bottom: 1.5rem;
  }

  .product-name {
    font-size: 3rem;
  }

  .product-description {
    font-size: 1rem;
  }

  .product-button {
    font-size: 1rem;
    padding: 0.7rem 1.2rem;
    border-radius: 25px;
  }
}

/* Desktop (min-width: 1024px) */
@media (min-width: 1024px) {
  .product-frame {
    padding: 2rem;
    border-radius: 15px;
  }

  .image-container {
    max-width: 300px;
    height: 300px;
    margin-bottom: 2rem;
  }

  .product-name {
    font-size: 3rem;
  }

  .product-description {
    font-size: 1.1rem;
  }

  .product-button {
    font-size: 1.1rem;
    padding: 0.8rem 1.5rem;
  }
}
</style>
