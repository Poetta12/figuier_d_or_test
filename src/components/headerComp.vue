<template>
  <header class="header">
    <div class="container">
      <!-- Bouton Toggle Light/Dark -->
      <!--<button class="theme-toggle-icon" @click="toggleTheme" aria-label="Toggle Theme">
        <span class="icon">
          <img
            :src="theme === 'dark' ? '/icons/bougie-eteinte.png' : '/icons/bougie-allumee.png'"
            alt="Figuier D'Or"
          />
        </span>
      </button>-->

      <BougieComp/>

      <!-- Logo -->
      <img
        class="logo"
        :src="theme === 'dark' ? '/logos/logo_2-removebg.png' : '/logos/logo-removebg.png'"
        alt="Figuier D'Or"
      />

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
import { ref, onMounted } from "vue";
import BougieComp from "@/components/BougieComp.vue";

// Sélection de l'élément <body>
let body;

// Assurez-vous que le body est disponible après le montage du composant
onMounted(() => {
  body = document.body;
});

// État pour le menu mobile
const isMenuOpen = ref(false);

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

// État pour le mode light/dark
const theme = ref("light");

const toggleTheme = () => {
  theme.value = theme.value === "dark" ? "light" : "dark";
  body.setAttribute("data-theme", theme.value);
};
</script>


<style scoped>
/* Général */

.icon {
  position: relative;
  display: inline-block;
}

.icon::after {
  content: '';
  position: absolute;
  bottom: -10px; /* Positionné légèrement en dessous de l'image */
  left: 50%;
  transform: translateX(-50%);
  width: 60px; /* Largeur de la base */
  height: 10px; /* Hauteur de la base */
  background: var(--color-darkgold);
  border-radius: 50%; /* Forme elliptique */
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.3); /* Ombre pour ajouter de la profondeur */
}

button:hover,
a:hover {
  cursor: none;
}

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
  align-self: flex-end;
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
  top: 0;
  right: -10px;
  width: 230%;
  transform: translateY(-200%);
  transition: transform 0.3s ease-in-out;
  z-index: 10;
}

.nav-list.open {
  transform: translateY(80%);
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
.theme-toggle-icon {
  background-color: transparent;
  border: none;
  border-radius: 5px;
  padding: 0.5rem 1rem 0;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.3s ease;
}

.theme-toggle-icon img {
  width: 60px; /* Taille ajustée */
  height: auto;
}

.theme-toggle-icon:hover {
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
  header{
    height: 15vh;
  }
  .nav-link {
    font-size: 1.5rem;
    width: fit-content;
  }

  .nav-link li {
    display: inline-block;
    width: fit-content;
  }

  .logo {
    max-width: 250px;
  }
}
</style>
