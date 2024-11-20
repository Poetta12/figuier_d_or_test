<template>
  <div class="holder" @click="toggleTheme">
    <div class="figue">
      <!-- Glow et flamme visibles uniquement en mode dark -->
      <div v-if="theme === 'dark'" class="blinking-glow"></div>
      <div class="thread"></div>
      <div v-if="theme === 'dark'" class="glow" :class="{ 'fade-in': isTransitioning }"></div>
      <div
        v-if="theme === 'dark'"
        class="flame"
        :class="{ 'grow-flame': isTransitioning }"
      ></div>

      <!-- Fumée visible uniquement en mode light -->
      <svg
        v-if="theme === 'light'"
        class="smoke"
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 100 200"
      >
        <path
          class="smoke-path layer1"
          d="M50 150 C 30 130, 70 110, 50 90 S 30 50, 50 30"
        />
        <path
          class="smoke-path layer2"
          d="M50 150 C 40 120, 60 100, 50 70 S 40 40, 50 20"
        />
        <path
          class="smoke-path layer3"
          d="M50 150 C 20 140, 80 120, 50 60 S 20 30, 50 10"
        />
      </svg>
    </div>
  </div>
</template>

<script setup>
import { ref, watch } from "vue";

// Gestion du thème
const theme = ref("light"); // Par défaut, mode clair
const isTransitioning = ref(false);

// Appliquer le thème sur le body
const updateThemeOnBody = () => {
  document.body.setAttribute("data-theme", theme.value);
};

// Surveiller les changements de thème
watch(theme, () => {
  updateThemeOnBody();
});

// Basculer le thème avec une animation
const toggleTheme = () => {
  isTransitioning.value = true;

  // Ajouter une transition pour la flamme ou la fumée
  setTimeout(() => {
    theme.value = theme.value === "dark" ? "light" : "dark";
    isTransitioning.value = false;
  }, 1000); // Durée de l'animation (1 seconde)
};

// Initialisation : appliquer le thème par défaut
updateThemeOnBody();
</script>

<style scoped>
/* Base pour la bougie */
.figue {
  position: relative;
  width: 40px;
  height: 50px;
  background: url('/src/assets/figue.png') no-repeat center center;
  background-size: cover;
}

.holder {
  width: 100px;
  position: relative;
  cursor: pointer;
  display: flex;
  justify-content: center;
}

.holder * {
  position: absolute;
  content: "";
}

.candle {
  width: 20px;
  height: 40px;
  border-radius: 75px / 20px;
  background: linear-gradient(#e48825, #e78e0e, #833c03, #4c1a03 50%, #1c0900);
}

.thread {
  width: 3px;
  height: 18px;
  top: -9px;
  left: 50%;
  border-radius: 40% 40% 0 0;
  transform: translateX(-50%);
  background: linear-gradient(#d6994a, #4b232c, #121212, black, #e8bb31 90%);
}

/* Flamme */
.flame {
  width: 7px;
  height: 40px;
  left: 50%;
  transform-origin: 50% 100%;
  transform: translateX(-50%);
  bottom: 100%;
  border-radius: 50% 50% 20% 20%;
  background: linear-gradient(white 80%, transparent);
  animation: moveFlame 6s linear infinite;
}

.grow-flame {
  animation: growFlame 0.8s ease-in-out;
}

@keyframes growFlame {
  0% {
    height: 0;
    opacity: 0;
  }
  100% {
    height: 45px;
    opacity: 1;
  }
}

/* Fumée SVG */
.smoke {
  position: absolute;
  top: -155px;
  left: 52%;
  width: 100px;
  height: 200px;
  transform: translateX(-50%);
}

.smoke-path {
  fill: none;
  stroke: rgba(50, 50, 50, 0.5);
  stroke-width: 2;
  stroke-dasharray: 200;
  stroke-dashoffset: 200;
  animation: smokeRise 4s ease-in-out infinite, drift 6s ease-in-out infinite;
}

.layer1 {
  animation-delay: 0s;
}

.layer2 {
  stroke-width: 1.5;
  animation-delay: 1s;
}

.layer3 {
  stroke-width: 1;
  animation-delay: 2s;
}

/* Animations */
@keyframes smokeRise {
  0% {
    stroke-dashoffset: 200;
    opacity: 0.5;
  }
  50% {
    opacity: 0.3;
  }
  100% {
    stroke-dashoffset: 0;
    opacity: 0;
  }
}

@keyframes drift {
  0% {
    transform: translateX(0);
  }
  25% {
    transform: translateX(-5px);
  }
  50% {
    transform: translateX(0);
  }
  75% {
    transform: translateX(5px);
  }
  100% {
    transform: translateX(0);
  }
}

/* Flamme */
@keyframes moveFlame {
  0%,
  100% {
    transform: translateX(-50%) rotate(-2deg);
  }
  50% {
    transform: translateX(-50%) rotate(2deg);
  }
}
</style>
