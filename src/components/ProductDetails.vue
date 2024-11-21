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
import FlameCursor from "@/components/FlameCursor.vue";

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

.modal-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.7);
  z-index: 1;
}

.modal-content {
  position: relative;
  background: var(--bg-color);
  color: var(--text-color);
  padding: 2rem;
  border-radius: 10px;
  width: 90%;
  max-width: 600px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
  z-index: 2;
  text-align: center;
}

.close-button {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: none;
  border: none;
  color: var(--text-color);
  font-size: 1.5rem;
}

.product-image {
  width: 100%;
  max-width: 300px;
  height: auto;
  margin-bottom: 1rem;
  border-radius: 8px;
}

.product-name {
  font-family: "Exo 2", cursive;
  font-size: 1.8rem;
  margin-bottom: 1rem;
}

.product-description {
  font-family: "Sour Gummy", sans-serif;
  font-size: 1rem;
  margin-bottom: 1.5rem;
}

.product-price {
  font-weight: bold;
  margin-bottom: 2rem;
}

.add-to-cart-button {
  padding: 0.8rem 1.5rem;
  font-family: "Sour Gummy", sans-serif;
  font-size: 1rem;
  background-color: var(--color-indigo);
  color: var(--text-color);
  border: none;
  border-radius: 5px;
  transition: background-color 0.3s ease, transform 0.3s ease;
}

.add-to-cart-button:hover {
  background-color: var(--color-lightgold);
  transform: scale(1.05);
}
</style>
