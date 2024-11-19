<template>
  <header class="header">
    <div class="container">
      <!-- Logo -->
      <img class="logo" src="/logos/logo_2-removebg.png" alt="Figuier D'Or" />


      <!-- Bouton Toggle Light/Dark -->
      <button class="theme-toggle" @click="toggleTheme">
        {{ theme === 'light' ? 'Mode Sombre' : 'Mode Clair' }}
      </button>

      <!-- Navigation -->
      <nav class="nav">
        <!-- Menu burger pour mobile -->
        <button class="menu-toggle" @click="toggleMenu" aria-label="Toggle Menu">
          <span :class="{ open: isMenuOpen }"></span>
          <span :class="{ open: isMenuOpen }"></span>
          <span :class="{ open: isMenuOpen }"></span>
        </button>

        <!-- Navigation List -->
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

// État pour le menu mobile
const isMenuOpen = ref(false);

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

// État pour le mode light/dark
const theme = ref("dark");

const toggleTheme = () => {
  theme.value = theme.value === "light" ? "dark" : "light";
  document.body.classList.toggle("light-mode", theme.value === "light");
};
</script>

<style scoped>
/* Styles globaux */
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
  border-bottom: 2px solid var(--color-lightgold);
  box-shadow: 0 4px 6px var(--color-darkgold);
}

/* Container */
.container {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

/* Logo */
.logo {
  max-width: 150px;
}

/* Menu Toggle (Burger pour Mobile) */
.menu-toggle {
  background: none;
  border: none;
  cursor: pointer;
  display: flex;
  flex-direction: column;
  gap: 4px;
  z-index: 11;
}

.menu-toggle span {
  width: 30px;
  height: 3px;
  background-color: var(--color-lightgold);
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

/* Navigation (Mobile) */
.nav {
  position: relative;
}

.nav-list {
  list-style: none;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 1rem;
  background-color: var(--bg-color);
  border: 1px solid var(--color-lightgold);
  border-radius: 8px;
  position: absolute;
  top: 100%;
  right: 0;
  width: 80%;
  transform: translateY(-200%);
  transition: transform 0.3s ease-in-out;
  z-index: 10;
}

.nav-list.open {
  transform: translateY(0);
}

.nav-link {
  font-size: 1rem;
  color: var(--color-lightgold);
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
  text-shadow: 0 1px 5px var(--color-lightgold);
}

/* Bouton Toggle Light/Dark */
.theme-toggle {
  background-color: var(--color-indigo);
  color: var(--text-color);
  border: none;
  border-radius: 5px;
  padding: 0.5rem 1rem;
  font-family: "Sour Gummy", sans-serif;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.3s ease;
}

.theme-toggle:hover {
  background-color: var(--color-lightgold);
  transform: scale(1.05);
}

/* Desktop Styles */
@media (min-width: 768px) {
  /* Cache le menu burger sur desktop */
  .menu-toggle {
    display: none;
  }

  .nav-list {
    position: static;
    flex-direction: row;
    justify-content: flex-end;
    width: auto;
    background: none;
    border: none;
    transform: translateY(0);
  }

  .nav-link {
    margin: 0 1rem;
    font-size: 1.2rem;
  }

  .logo {
    max-width: 200px;
  }
}

@media (min-width: 1024px) {
  .nav-link {
    font-size: 1.5rem;
    margin: 0 1.5rem;
  }

  .logo {
    max-width: 250px;
  }
}
</style>
