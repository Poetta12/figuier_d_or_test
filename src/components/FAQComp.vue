<template>
  <section class="faq">
    <h2 class="faq-title">Questions Fréquemment Posées</h2>
    <div class="faq-list">
      <div v-for="(item, index) in faqItems" :key="index" class="faq-item">
        <button class="faq-question" @click="toggleAnswer(index)">
          {{ item.question }}
          <span class="faq-icon">{{ openedIndex === index ? "-" : "+" }}</span>
        </button>
        <div v-if="openedIndex === index" class="faq-answer">
          <p>{{ item.answer }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from "vue";

const faqItems = ref([
  {
    question: "Quels matériaux utilisez-vous pour fabriquer vos bougies ?",
    answer:
      "Nos bougies sont fabriquées à partir de cire 100% naturelle, principalement de la cire de soja, et des mèches en coton sans plomb pour garantir une combustion propre.",
  },
  {
    question: "Proposez-vous des bougies personnalisées ?",
    answer:
      "Oui, nous proposons des bougies personnalisées pour des événements spéciaux comme les mariages, anniversaires ou fêtes d'entreprise. Contactez-nous pour plus de détails.",
  },
  {
    question: "Quels parfums sont disponibles dans votre boutique ?",
    answer:
      "Nous avons une large gamme de parfums, allant des classiques comme la vanille et la lavande aux exclusifs comme figue dorée et bois de oud.",
  },
  {
    question: "Comment dois-je entretenir mes bougies ?",
    answer:
      "Coupez la mèche à 5 mm avant chaque utilisation pour une combustion uniforme. Évitez de laisser une bougie allumée plus de 4 heures d'affilée.",
  },
  {
    question: "Quels sont vos délais de livraison ?",
    answer:
      "Nous livrons en 3 à 5 jours ouvrés en France métropolitaine. Pour les commandes personnalisées, un délai supplémentaire peut être nécessaire.",
  },
  {
    question: "Vos bougies sont-elles écologiques ?",
    answer:
      "Oui, nous utilisons des matériaux respectueux de l'environnement, des emballages recyclables et nous privilégions les fournisseurs locaux.",
  },
  {
    question: "Puis-je retourner ou échanger un article ?",
    answer:
      "Les articles non personnalisés peuvent être retournés ou échangés sous 14 jours après réception, à condition qu'ils soient non utilisés.",
  },
]);

const openedIndex = ref(null);

const toggleAnswer = (index) => {
  openedIndex.value = openedIndex.value === index ? null : index;
};
</script>

<style scoped>
.faq {
  padding: 2rem;
  background: var(--bg-color);
  color: var(--text-color);
  border-radius: 12px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  max-width: 800px;
  margin: auto;
}

.faq-title {
  text-align: center;
  font-size: 2rem;
  font-weight: 600;
  margin-bottom: 1.5rem;
  color: var(--color-lightgold);
}

.faq-list {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.faq-item {
  border: 1px solid rgba(0, 0, 0, 0.1);
  border-radius: 8px;
  overflow: hidden;
  transition: box-shadow 0.3s ease, transform 0.3s ease;
}

.faq-item:hover {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  transform: translateY(-2px);
}

.faq-question {
  width: 100%;
  text-align: left;
  padding: 1rem;
  background: var(--color-indigo);
  color: var(--color-lightgold);
  font-size: 1rem;
  border: none;
  display: flex;
  justify-content: space-between;
  align-items: center;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.faq-question:hover {
  background: var(--color-darkgold);
}

.faq-icon {
  font-size: 1.5rem;
}

.faq-answer {
  padding: 1rem;
  background: var(--color-bg-transp);
  color: var(--text-color);
  font-size: 0.9rem;
  line-height: 1.5;
}
</style>
