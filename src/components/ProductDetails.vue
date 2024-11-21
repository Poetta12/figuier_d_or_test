<template>
  <div class="product-details-modal" v-if="isVisible">
    <div class="modal-overlay" @click="closeDetails"></div>
    <div class="modal-content">
      <button class="close-button" @click="closeDetails">&times;</button>
      <img class="product-image" :src="product.image" :alt="product.name" />
      <h2 class="product-name">{{ product.name }}</h2>
      <p class="product-description">{{ product.description }}</p>
      <p class="product-price" v-if="product.price">Prix : {{ product.price }} €</p>
      <button class="add-to-cart-button" @click="addToCart">Ajouter au panier</button>
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from "vue";

// Propriétés reçues par le composant
defineProps({
  product: {
    type: Object,
    required: true,
  },
  isVisible: {
    type: Boolean,
    required: true,
  },
});

// Événements émis par le composant
const emit = defineEmits(["close", "addToCart"]);

// Ferme la fenêtre modale
const closeDetails = () => {
  emit("close");
};

// Ajoute le produit au panier
const addToCart = () => {
  emit("addToCart", product); // Passe 'product' comme argument de l'événement
};
</script>

<style scoped>
/* Mobile-first styles */

/* Conteneur principal de la modale */
.product-details-modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

/* Fond d'overlay */
.modal-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.7);
  z-index: 1;
}

/* Contenu de la modale */
.modal-content {
  position: relative;
  background: var(--bg-color);
  color: var(--text-color);
  padding: 1.5rem;
  border-radius: 10px;
  width: 90%;
  max-width: 360px; /* Taille max sur mobile */
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
  z-index: 2;
  text-align: center;
}

/* Bouton de fermeture */
.close-button {
  position: absolute;
  top: 0.5rem;
  right: 0.5rem;
  background: none;
  border: none;
  color: var(--text-color);
  font-size: 1.5rem;
  cursor: pointer;
}

/* Image du produit */
.product-image {
  width: 100%;
  height: auto;
  margin-bottom: 1rem;
  border-radius: 8px;
}

/* Nom du produit */
.product-name {
  font-family: "Exo 2", cursive;
  font-size: 1.5rem;
  margin-bottom: 0.5rem;
}

/* Description */
.product-description {
  font-family: "Sour Gummy", sans-serif;
  font-size: 0.9rem;
  margin-bottom: 1rem;
}

/* Prix */
.product-price {
  font-weight: bold;
  font-size: 1rem;
  margin-bottom: 1.5rem;
}

/* Bouton "Ajouter au panier" */
.add-to-cart-button {
  padding: 0.5rem 1rem;
  font-family: "Sour Gummy", sans-serif;
  font-size: 0.9rem;
  background-color: var(--color-indigo);
  color: var(--text-color);
  border: none;
  border-radius: 20px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.3s ease;
}

.add-to-cart-button:hover {
  background-color: var(--color-lightgold);
  transform: scale(1.05);
}

/* Responsive styles */

/* Tablettes (min-width: 768px) */
@media (min-width: 768px) {
  .modal-content {
    max-width: 500px;
    padding: 2rem;
  }

  .product-name {
    font-size: 1.8rem;
  }

  .product-description {
    font-size: 1rem;
  }

  .add-to-cart-button {
    font-size: 1rem;
    padding: 0.7rem 1.5rem;
  }
}

/* Desktop (min-width: 1024px) */
@media (min-width: 1024px) {
  .modal-content {
    max-width: 600px;
    padding: 2.5rem;
  }

  .product-name {
    font-size: 2rem;
  }

  .product-description {
    font-size: 1.1rem;
  }

  .add-to-cart-button {
    font-size: 1.1rem;
    padding: 0.8rem 2rem;
  }
}
</style>
