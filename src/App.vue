<template>
  <div id="app">
    <FlameCursor />
    <header-comp/>
    <div class="wrapper">
      <router-view />
    </div>
    <figue-comp/>
  </div>
</template>

<script setup>
/* Pas de logique pour l'instant */
import HeaderComp from "@/components/headerComp.vue";
import FlameCursor from "@/components/FlameCursor.vue";
import FigueComp from "@/components/figueComp.vue";
</script>

<style scoped>
.wrapper{
  max-width: 1200px;
  margin: auto;
}
</style>
