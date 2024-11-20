<template>
  <div class="home">

    <BannerComp />
    <div class="wrapper">
      <CollectionsComp />
    </div>



    <footer class="footer">
      <p>&copy; 2024 Figuier D'Or. Tous droits réservés.</p>
    </footer>
  </div>
</template>

<script setup>
import CollectionsComp from "@/components/CollectionsComp.vue";
import BannerComp from "@/components/BannerComp.vue";
</script>

<style scoped>
.footer {
  text-align: center;
  margin-top: 2rem;
  color: var(--color-indigo);
  font-size: 0.9rem;
}
</style>
