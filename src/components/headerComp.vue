<template>
  <header class="header">
    <div class="container">
      <img class="logo" src="/logos/logo-removebg.png" alt="Figuier D'Or">
      <nav class="nav">
        <button class="menu-toggle" @click="toggleMenu">
          <span :class="{ open: isMenuOpen }"></span>
        </button>
        <ul :class="{ 'nav-list': true, open: isMenuOpen }">
          <li>
            <router-link to="/" class="nav-link" exact-active-class="active">Accueil</router-link>
          </li>
          <li>
            <router-link to="/about" class="nav-link" exact-active-class="active">À propos</router-link>
          </li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<script setup>
import { ref } from "vue";

const isMenuOpen = ref(false);

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};
</script>

<style scoped>
/* Palette principale */
:root {
  --color-black: #000000;
  --color-gold: #FFD700;
  --color-bordeaux: #800020;
  --color-indigo: #4B0082;

  --text-color: #FFFFFF;
  --bg-color: var(--color-black);
}

/* Styles globaux pour le header */
.header {
  background-color: var(--bg-color);
  color: var(--text-color);
  padding: 1rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  position: sticky;
  top: 0;
  z-index: 10;
  border-bottom: 1px solid var(--color-gold);
}

.container {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

/* Logo */
.logo {
  max-width: 120px;
}

/* Menu Toggle (Mobile) */
.menu-toggle {
  background: none;
  border: none;
  cursor: pointer;
  display: flex;
  flex-direction: column;
  gap: 4px;
  position: relative;
  z-index: 11;
}

.menu-toggle span {
  width: 30px;
  height: 3px;
  background-color: var(--color-gold);
  border-radius: 2px;
  transition: all 0.3s ease;
}

.menu-toggle span.open:nth-child(1) {
  transform: rotate(45deg) translate(5px, 5px);
}

.menu-toggle span.open:nth-child(2) {
  opacity: 0;
}

.menu-toggle span.open:nth-child(3) {
  transform: rotate(-45deg) translate(5px, -5px);
}

/* Navigation */
.nav {
  position: absolute;
  top: 100%;
  right: 0;
  background-color: var(--bg-color);
  width: 100%;
  transition: transform 0.3s ease-in-out;
}

.nav-list {
  list-style: none;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 1rem;
  transform: translateY(-200%);
}

.nav-list.open {
  transform: translateY(0);
}

/* Navigation Links */
.nav-link {
  font-family: "Tan Tangkiewood", serif;
  font-size: 1.2rem;
  color: var(--color-gold);
  text-decoration: none;
  margin: 0.5rem 0;
  transition: color 0.3s ease;
}

.nav-link.active {
  font-weight: bold;
  text-decoration: underline;
  color: var(--color-indigo);
}

.nav-link:hover {
  color: var(--color-bordeaux);
}

/* Desktop View */
@media (min-width: 768px) {
  .menu-toggle {
    display: none;
  }

  .nav {
    position: static;
    display: flex;
  }

  .nav-list {
    flex-direction: row;
    transform: translateY(0);
  }

  .nav-link {
    margin: 0 1rem;
    font-size: 1.5rem;
  }
}
</style>
