<template>
  <div class="home">

    <CarouselComp />
    <CollectionsComp />

    <footer class="footer">
      <p>&copy; 2024 Figuier D'Or. Tous droits réservés.</p>
    </footer>
  </div>
</template>

<script setup>
import CarouselComp from "@/components/CarouselComp.vue";
import CollectionsComp from "@/components/CollectionsComp.vue";
</script>

<style scoped>
.footer {
  text-align: center;
  margin-top: 2rem;
  color: var(--color-indigo);
  font-size: 0.9rem;
}
</style>
