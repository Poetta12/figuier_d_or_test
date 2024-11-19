<template>
  <div id="app">
    <FlameCursor />
    <header-comp/>
    <div class="wrapper">
      <router-view />
    </div>
  </div>
</template>

<script setup>
/* Pas de logique pour l'instant */
import HeaderComp from "@/components/headerComp.vue";
import FlameCursor from "@/components/FlameCursor.vue";
</script>

<style scoped>
.wrapper{
  max-width: 1000px;
  margin: auto;
}

/* Mode bureau uniquement */
@media (min-width: 1024px) {
  body[data-theme="dark"]{
    background: var(--img-bg-light);
    background-size: cover;
  }
  body[data-theme="light"]{
    background: var(--img-bg-light);
    background-size: cover;
  }
}
</style>
