<template>
  <div id="app">
    <header-comp/>
    <div class="wrapper">
      <router-view />
    </div>
  </div>
</template>

<script setup>
/* Pas de logique pour l'instant */
import HeaderComp from "@/components/headerComp.vue";
</script>

<style scoped>
.wrapper{
  max-width: 1200px;
  margin: auto;
}
</style>
