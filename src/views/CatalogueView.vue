<template>
  <div class="catalogue-page">
    <h1 class="catalogue-title">Catalogue des Bougies Artisanales</h1>
    <div class="products-grid">
      <ProductFrame
        v-for="product in products"
        :key="product.id"
        :image="product.image"
        :name="product.name"
        :description="product.description"
        :buttonText="'Découvrir'"
        @actionClick="showDetails(product)"
      />
    </div>

    <!-- Composant ProductDetails -->
    <ProductDetails
      v-if="selectedProduct"
      :product="selectedProduct"
      :isVisible="isModalVisible"
      @close="closeModal"
      @addToCart="addToCart"
    />
  </div>
</template>

<script setup>
import ProductFrame from "@/components/ProductFrame.vue";
import ProductDetails from "@/components/ProductDetails.vue";
import { ref } from "vue";
import FlameCursor from "@/components/FlameCursor.vue";

// Liste des produits
const products = [
  {
    id: 1,
    name: "Bougie Élégante",
    description: "Une bougie raffinée pour illuminer vos soirées.",
    image: "src/assets/img/bougies/B10.jpg",
  },
  {
    id: 2,
    name: "Bougie Artisanale",
    description: "Fabriquée à la main avec des matériaux de qualité.",
    image: "src/assets/img/bougies/B11.jpg",
  },
  {
    id: 3,
    name: "Bougie Naturelle",
    description: "Parfum doux et naturel pour un moment de détente.",
    image: "src/assets/img/bougies/B12.jpg",
  },
  {
    id: 4,
    name: "Bougie Festive",
    description: "Parfaite pour célébrer vos événements spéciaux.",
    image: "src/assets/img/bougies/B13.jpg",
  },
  {
    id: 5,
    name: "Bougie Minimaliste",
    description: "Un design simple et épuré, idéal pour votre intérieur.",
    image: "src/assets/img/bougies/B15.jpg",
  },
];
// Gestion de la fenêtre modale
const selectedProduct = ref(null);
const isModalVisible = ref(false);

const showDetails = (product) => {
  selectedProduct.value = product;
  isModalVisible.value = true;
};

const closeModal = () => {
  isModalVisible.value = false;
  selectedProduct.value = null;
};

const addToCart = (product) => {
  console.log("Ajouté au panier :", product);
  closeModal();
};
</script>

<style scoped>
.catalogue-page {
  padding: 2rem;
  background-color: var(--bg-color);
  color: var(--text-color);
}

.catalogue-title {
  text-align: center;
  font-family: "Exo 2", cursive;
  font-size: 2rem;
  margin-bottom: 2rem;
}

.products-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}
</style>
