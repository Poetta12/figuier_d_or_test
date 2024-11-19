<template>
  <header class="header">
    <div class="container">
<<<<<<< HEAD
      <img class="logo" src="/logos/logo_2-removebg.png" alt="Figuier D'Or">
=======
      <!-- Logo -->
      <img
        class="logo"
        :src="theme === 'dark' ? '/logos/logo_2-removebg.png' : '/logos/logo-removebg.png'"
        alt="Figuier D'Or"
      />

      <!-- Bouton Toggle Light/Dark -->
      <button class="theme-toggle" @click="toggleTheme">
        {{ theme === 'dark' ? 'Mode clair' : 'Mode sombre' }}
      </button>

      <!-- Navigation -->
>>>>>>> a035d82bd60eec956ffa02b9261713ff7d8be08f
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
const theme = ref("light");

const toggleTheme = () => {
  theme.value = theme.value === "dark" ? "light" : "dark";
  document.documentElement.setAttribute("data-theme", theme.value);
};
</script>

<<<<<<< HEAD
<style scoped>
/* Styles globaux pour le header */
=======

<style scoped>
/* Général */
:root {
  --color-black: #111;
  --color-lightgold: #f4b52b;
  --color-darkgold: #bd6513;
  --color-bordeaux: #850000;
  --color-indigo: #402978;

  --text-color: antiquewhite;
  --bg-color: var(--color-black);
}

[data-theme="light"] {
  --color-black: #f9f9f9;
  --color-lightgold: #ffcc00;
  --color-darkgold: #d4a017;
  --color-bordeaux: #d94f4f;
  --color-indigo: #6b4fa7;

  --text-color: #111;
  --bg-color: #ffffff;
}

button:hover,
a:hover {
  cursor: none;
}

/* Styles globaux */
>>>>>>> a035d82bd60eec956ffa02b9261713ff7d8be08f
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
<<<<<<< HEAD
  border-bottom: 1px solid var(--color-dark-gold); /* Dark gold */
=======
  border-bottom: 2px solid var(--color-lightgold);
  box-shadow: 0 4px 6px var(--color-darkgold);
>>>>>>> a035d82bd60eec956ffa02b9261713ff7d8be08f
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
<<<<<<< HEAD
  background-color: var(--color-light-gold); /* Light gold */
=======
  background-color: var(--color-lightgold);
>>>>>>> a035d82bd60eec956ffa02b9261713ff7d8be08f
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
  width: 230%;
  transform: translateY(-200%);
  transition: transform 0.3s ease-in-out;
  z-index: 10;
}

.nav-list.open {
  transform: translateY(0);
}

.nav-link {
<<<<<<< HEAD
  font-family: "Tan Tangkiewood", serif;
  font-size: 1.2rem;
  color: var(--color-light-gold); /* Light gold */
=======
  font-size: 1rem;
  color: var(--color-lightgold);
>>>>>>> a035d82bd60eec956ffa02b9261713ff7d8be08f
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
<<<<<<< HEAD
  color: var(--color-dark-gold); /* Dark gold on hover */
=======
  color: var(--color-bordeaux);
  text-shadow: 0 1px 5px var(--color-lightgold);
>>>>>>> a035d82bd60eec956ffa02b9261713ff7d8be08f
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
    font-size: 1.2rem;
  }

  .logo {
    max-width: 200px;
  }
}

@media (min-width: 1024px) {
  .nav-link {
    font-size: 1.5rem;
    width: fit-content;
  }

  .nav-link li{
    display: inline-block;
    width: fit-content;
  }

  .logo {
    max-width: 250px;
  }
}
</style>
