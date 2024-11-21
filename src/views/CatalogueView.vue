<template>
  <div class="catalogue-page">
    <h1 class="catalogue-title">Catalogue des Bougies Artisanales</h1>
    <div class="products-grid">
      <ProductFrame
        v-for="product in paginatedProducts"
        :key="product.id"
        :image="product.image"
        :name="product.name"
        :description="product.description"
        :buttonText="'Découvrir'"
        @actionClick="showDetails(product)"
      />
    </div>

    <!-- Pagination -->
    <PaginationComp
      :currentPage="currentPage"
      :totalPages="totalPages"
      @changePage="goToPage"
    />

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
import PaginationComp from "@/components/PaginationComp.vue";
import productsData from "/database/bougies.json";
import { ref, computed } from "vue";

// Gestion de la fenêtre modale
const products = ref(productsData);
const selectedProduct = ref(null);
const isModalVisible = ref(false);

// Pagination variables
const currentPage = ref(1);
const itemsPerPage = 9; // Nombre d'éléments par page

// Calcul des pages
const totalPages = computed(() => Math.ceil(products.value.length / itemsPerPage));
const paginatedProducts = computed(() => {
  const start = (currentPage.value - 1) * itemsPerPage;
  return products.value.slice(start, start + itemsPerPage);
});

// Actions pour la pagination
const goToPage = (page) => {
  if (page >= 1 && page <= totalPages.value) {
    currentPage.value = page;
  }
};

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
/* Base styles for mobile-first design */

.catalogue-page {
  max-width: 1200px;
  margin: auto;
  padding: 1rem;
  background-color: var(--bg-color);
  color: var(--text-color);
}

.catalogue-title {
  text-align: center;
  font-size: 2rem;
  margin-bottom: 1.5rem;
}

.products-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1rem;
}

/* Responsive styles for tablets */
@media (min-width: 768px) {
  .catalogue-page {
    padding: 2rem;
  }

  .catalogue-title {
    font-size: 2rem;
    margin-bottom: 2rem;
  }

  .products-grid {
    gap: 1.5rem;
  }
}

/* Responsive styles for desktops */
@media (min-width: 1024px) {
  .catalogue-title {
    font-size: 4rem;
  }

  .products-grid {
    gap: 2rem;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  }
}
</style>
