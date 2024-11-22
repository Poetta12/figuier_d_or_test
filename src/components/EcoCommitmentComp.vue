<template>
  <section class="eco-commitment">
    <h2 class="eco-title">Notre Engagement Écologique</h2>
    <div class="eco-wrapper">
      <p>
        Chez <strong>Figuier d'Or</strong>, nous croyons en la création de produits
        respectueux de l'environnement et de votre bien-être. Nos bougies sont fabriquées
        avec des matériaux naturels et durables, garantissant une empreinte écologique minimale.
      </p>
      <div class="eco-content">
        <div class="eco-text">
          <ul class="eco-group">
            <li>
              <div class="icon-group">
                <i class="fas fa-leaf"></i>
                <p><strong>Cire Naturelle :</strong></p>
              </div>
              <p>Nous utilisons principalement de la cire de soja et de la cire d'abeille, sans additifs chimiques nocifs.</p>
            </li>
            <li>
              <div class="icon-group">
                <i class="fas fa-recycle"></i>
                <p><strong>Emballages Écoresponsables :</strong></p>
              </div>
              <p>Nos emballages sont 100% recyclables et conçus pour réduire les déchets.</p>
            </li>
            <li>
              <div class="icon-group">
                <i class="fas fa-tree"></i>
                <p><strong>Approvisionnement Local :</strong></p>
              </div>
              <p>Nous privilégions des matières premières issues de fournisseurs locaux pour limiter notre impact carbone.</p>
            </li>
          </ul>
        </div>
        <div class="eco-image">
          <img src="/deco_img/eco.webp" alt="Engagement écologique" />
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
</script>

<style scoped>
/* Section principale */
.eco-commitment {
  padding: 2rem 1rem;
  background: var(--color-bg-transp);
  color: var(--text-color);
  border-radius: 12px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  gap: 2rem;
  max-width: 1200px;
  margin: 2rem auto;
}

/* Titre principal */
.eco-title {
  text-align: center;
  font-size: 3rem;
  font-family: 'Tangerine', cursive;
  font-weight: bold;
  color: var(--color-bordeaux);
  margin-bottom: 1.5rem;
}

/* Wrapper de contenu */
.eco-wrapper > p {
  margin-bottom: 2rem;
  font-size: 1.2rem;
  line-height: 1.8;
  color: var(--text-color);
}

.eco-content {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

/* Contenu texte */
.eco-text {
  flex: 1;
}

.eco-group {
  margin: 0;
  padding: 0;
  list-style: none;
}

.eco-group li {
  margin-bottom: 2rem;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  color: var(--text-color);
  font-size: 1rem;
}

.icon-group {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.icon-group i {
  font-size: 1.5rem;
  color: var(--color-lightgold);
}

/* Image */
.eco-image {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}

.eco-image img {
  max-width: 100%;
  border-radius: 12px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.eco-image img:hover {
  transform: scale(1.05);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
}

/* Responsive Styles */
@media (min-width: 768px) {
  .eco-content {
    flex-direction: row;
    gap: 3rem;
  }

  .eco-text {
    flex: 2;
  }

  .eco-image {
    flex: 1;
  }
}
</style>
