<template>
  <div class="carousel" @mouseover="stopSlideShow" @mouseleave="startSlideShow">
    <div class="carousel-track" :style="{ transform: `translateX(-${currentSlide * 100}%)` }">
      <img v-for="(image, index) in images" :key="index" :src="image" :alt="'Produit ' + (index + 1)" />
    </div>

    <!-- Boutons de navigation -->
    <button class="carousel-button prev" @click="prevSlide">&#10094;</button>
    <button class="carousel-button next" @click="nextSlide">&#10095;</button>

    <!-- Indicateurs -->
    <div class="carousel-indicators">
      <span
        v-for="(image, index) in images"
        :key="index"
        class="indicator"
        :class="{ active: index === currentSlide }"
        @click="goToSlide(index)"
      ></span>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";

// Images pour le carrousel
const images = [
  "/src/assets/img/candle4.jpeg",
  "/src/assets/img/candle5.jpeg",
  "/src/assets/img/candle6.jpeg",
  "/img/candle4.jpeg",
  "/img/candle5.jpeg",
  "/img/candle6.jpeg",
];

// État réactif pour le slide actuel
const currentSlide = ref(0);
let slideInterval = null;

// Méthodes du carrousel
const nextSlide = () => {
  currentSlide.value = (currentSlide.value + 1) % images.length;
};

const prevSlide = () => {
  currentSlide.value = (currentSlide.value - 1 + images.length) % images.length;
};

const goToSlide = (index) => {
  currentSlide.value = index;
};

const startSlideShow = () => {
  slideInterval = setInterval(() => {
    nextSlide();
  }, 3000); // Change de slide toutes les 3 secondes
};

const stopSlideShow = () => {
  clearInterval(slideInterval);
};

// Lifecycle hooks
onMounted(() => {
  startSlideShow();
});

onBeforeUnmount(() => {
  stopSlideShow();
});
</script>

<style scoped>
.carousel {
  position: relative;
  width: 100%;
  max-height: 500px;
  overflow: hidden;
  margin: 0 0 1rem;
}

.carousel-track {
  display: flex;
  transition: transform 0.5s ease-in-out;
  width: 100%;
}

.carousel-track img {
  width: 100%;
  height: auto;
  flex-shrink: 0;
}

.carousel-button {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background-color: rgba(0, 0, 0, 0.5);
  border: none;
  color: white;
  padding: 0.5rem 1rem;
  cursor: pointer;
  z-index: 2;
  font-size: 1.5rem;
}

.carousel-button.prev {
  left: 1rem;
}

.carousel-button.next {
  right: 1rem;
}

.carousel-indicators {
  position: absolute;
  bottom: 1rem;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 0.5rem;
}

.indicator {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background-color: rgba(50, 100, 100, 0.5);
  cursor: pointer;
}

.indicator.active {
  background-color: var(--color-indigo);
}
</style>
