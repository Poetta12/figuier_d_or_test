<template>
  <header class="header">
    <div class="container">
      <img class="logo" src="/logos/logo-removebg.png" alt="Figuier D'Or">
      <h1 class="subtitle">Bougies artisanales pour illuminer vos moments.</h1>
      <nav class="nav">
        <router-link to="/" class="nav-link" exact-active-class="active">Accueil</router-link>
        <router-link to="/about" class="nav-link" exact-active-class="active">À propos</router-link>
      </nav>
    </div>

  </header>
</template>

<script setup>
</script>

<style scoped>
.logo{
  width: 200px;
}
.container{
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 50px;
}
.header {
  border-bottom: 1px solid var(--color-gold);
  text-align: center;
  background-color: var(--color-bordeaux);
  padding: 1rem 0;
  color: var(--color-gold);
}

.title {
  font-family: "Nexa Script", cursive;
  color: var(--color-gold);
  font-size: 3rem;
}

.subtitle {
  font-family: "Tan Tangkiewood", serif;
  color: var(--text-color);
  font-size: 2rem;
}

.nav {
  margin-top: 1rem;
  display: flex;
  justify-content: center;
  gap: 2rem;
}

.nav-link {
  font-family: "Tan Tangkiewood", serif;
  color: var(--color-gold);
  text-decoration: none;
  font-size: 1.5rem;
}

.nav-link.active {
  font-weight: bold;
  text-decoration: underline;
}
</style>
