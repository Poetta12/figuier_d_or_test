<template>
  <div>
    <!-- Curseur flamme -->
    <div
      class="holder"
      :class="{ 'is-hovering': isHovering }"
      :style="{ top: cursorY + 'px', left: cursorX + 'px' }"
    >
      <!-- La figue remplace la bougie -->
      <div class="figue">
        <div class="blinking-glow"></div>
        <div class="thread"></div>
        <div class="flame"></div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";

// Variables pour la position du curseur et état de hover
const cursorX = ref(0);
const cursorY = ref(0);
const isHovering = ref(false);

// Mise à jour de la position du curseur
const updateCursor = (event) => {
  cursorX.value = event.clientX;
  cursorY.value = event.clientY + 50;
};

// Activer/désactiver l'état de hover
const handleHover = () => {
  isHovering.value = true;
};

const handleHoverOut = () => {
  isHovering.value = false;
};

// Ajouter les écouteurs pour suivre les interactions
onMounted(() => {
  window.addEventListener("mousemove", updateCursor);

  // Ajouter des écouteurs pour tous les boutons et liens
  document.querySelectorAll("button, a").forEach((el) => {
    el.addEventListener("mouseenter", handleHover);
    el.addEventListener("mouseleave", handleHoverOut);
  });
});

onBeforeUnmount(() => {
  window.removeEventListener("mousemove", updateCursor);

  // Retirer les écouteurs pour les boutons et liens
  document.querySelectorAll("button, a").forEach((el) => {
    el.removeEventListener("mouseenter", handleHover);
    el.removeEventListener("mouseleave", handleHoverOut);
  });
});
</script>

<style scoped>
/* Conteneur principal */
.holder {
  position: fixed;
  width: 25px;
  height: 80px;
  transform: translate(-50%, -50%);
  pointer-events: none;
  z-index: 9999;
}

/* Corps de la figue */
.figue {
  position: relative;
  width: 40px;
  height: 50px;
  background: url('/src/assets/figue.png') no-repeat center center;
  background-size: cover;
}

/* Mèche */
.thread {
  position: absolute;
  width: 1px;
  height: 8px;
  top: -5px;
  left: 50%;
  z-index: 1;
  border-radius: 40% 40% 0 0;
  transform: translateX(-50%);
  background: linear-gradient(#d6994a, #4b232c, #121212, black, #e8bb31 90%);
}

/* Flamme réduite */
.flame {
  position: absolute;
  width: 8px; /* Réduit légèrement la largeur */
  height: 15px; /* Réduit légèrement la hauteur */
  left: 50%;
  transform-origin: 50% 100%;
  transform: translateX(-50%);
  bottom: 100%;
  border-radius: 50% 50% 20% 20%;
  background: linear-gradient(white 80%, transparent);
  animation: moveFlame 3s linear infinite, enlargeFlame 2s linear infinite;
  transition: all 0.3s ease;
}

.flame:before {
  content: "";
  position: absolute;
  width: 100%;
  height: 100%;
  border-radius: 50% 50% 20% 20%;
  box-shadow: 0 0 5px 0 rgba(247, 93, 0, 0.4), 0 -2px 1px 0 rgba(247, 128, 0, 0.7);
  transition: all 0.3s ease;
}

/* Flamme agrandie en hover */
.is-hovering .flame {
  height: 50px; /* Ajuste la taille agrandie */
  width: 10px; /* Ajuste la largeur agrandie */
}

.is-hovering .flame:before {
  box-shadow: 0 0 10px 0 rgba(247, 93, 0, 0.7), 0 -3px 2px 0 rgba(247, 128, 0, 0.9);
}

/* Animations */
@keyframes moveFlame {
  0%,
  100% {
    transform: translateX(-50%) rotate(-2deg);
  }
  50% {
    transform: translateX(-50%) rotate(2deg);
  }
}

@keyframes enlargeFlame {
  0%,
  100% {
    height: 25px;
  }
  50% {
    height: 28px;
  }
}

/* Lueur autour de la flamme */
.blinking-glow {
  position: absolute;
  width: 25px;
  height: 50px;
  left: 50%;
  top: -50%;
  transform: translateX(-50%);
  border-radius: 50%;
  background: #ff6000;
  filter: blur(12px); /* Réduction du flou */
  animation: blinkIt 0.1s infinite;
}

@keyframes blinkIt {
  50% {
    opacity: 0.8;
  }
}
</style>
