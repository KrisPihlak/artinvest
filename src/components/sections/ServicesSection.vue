<script setup lang="ts">
const pillars = [
  { verb: 'Aitame lihtsustada', detail: 'Tööprotsesside lihtsustamine ja olemasolevate protsesside parandamine.' },
  { verb: 'Aitame korrastada', detail: 'Selge ülevaade, nähtav töövoog ja vähem segadust igapäevatöös.' },
  { verb: 'Aitame digitaliseerida', detail: 'Praktilised infosüsteemid ja digitaliseerimine, mis toetab päris tööd.' },
  { verb: 'Aitame ehitada', detail: 'Väiksemad veebilahendused, veebilehed ja vajalikud tööriistad.' },
  { verb: 'Aitame toetada', detail: 'Tehniline tugi ja pidev partnerlus, kui organisatsioon kasvab.' },
]

const offerings = [
  'Tööprotsesside lihtsustamine',
  'Digitaliseerimine',
  'Väiksemad veebilahendused ja veebilehed',
  'Praktilised infosüsteemid',
  'Tehniline tugi',
  'Olemasolevate protsesside parandamine',
]
</script>

<template>
  <section id="teenused" class="section services">
    <div class="section-inner">
      <span class="section-label">Teenused</span>
      <h2 class="section-title">Mida me teeme</h2>
      <p class="section-lead">
        Me ei müü ainult veebilehti, tarkvaraarendust või IT-teenuseid. Meie eesmärk on aidata
        organisatsioonidel töötada lihtsamalt, kiiremini ja väiksema segadusega.
      </p>
      <p class="section-audiences">
        Töötame kohalike ettevõtete, hooldus- ja tehnikafirmade, MTÜ-de, haridusasutuste ja
        omavalitsustega.
      </p>

      <div class="pillars">
        <article v-for="pillar in pillars" :key="pillar.verb" class="pillar">
          <h3 class="pillar-verb">{{ pillar.verb }}</h3>
          <p class="pillar-detail">{{ pillar.detail }}</p>
        </article>
      </div>

      <div class="offerings-block">
        <h3 class="offerings-title">Konkreetselt saame aidata</h3>
        <ul class="offerings-list">
          <li v-for="item in offerings" :key="item">{{ item }}</li>
        </ul>
      </div>
    </div>
  </section>
</template>

<style scoped>
.services {
  background: var(--color-surface);
}

.section-audiences {
  margin-top: 0.75rem;
  font-size: 0.9375rem;
  color: var(--color-text-tertiary);
  line-height: 1.5;
  max-width: 42rem;
}

.pillars {
  margin-top: 2rem;
  display: flex;
  flex-direction: column;
  gap: 0;
  border: 1px solid var(--color-border-light);
  border-radius: var(--radius-lg);
  overflow: hidden;
}

@media (min-width: 768px) {
  .pillars {
    margin-top: 3rem;
  }
}

.pillar {
  padding: 1.25rem 1.375rem;
  border-bottom: 1px solid var(--color-border-light);
}

@media (min-width: 768px) {
  .pillar {
    padding: 1.75rem 2rem;
  }
}

.pillar:last-child {
  border-bottom: none;
}

.pillar-verb {
  font-size: 1.1875rem;
  font-weight: 600;
  letter-spacing: -0.02em;
  color: var(--color-text);
  text-wrap: balance;
}

@media (min-width: 768px) {
  .pillar-verb {
    font-size: 1.375rem;
  }
}

.pillar-detail {
  margin-top: 0.375rem;
  font-size: 0.9375rem;
  color: var(--color-text-secondary);
  line-height: 1.5;
}

.offerings-block {
  margin-top: 3.5rem;
}

.offerings-title {
  font-size: 1.25rem;
  font-weight: 600;
}

.offerings-list {
  margin: 1.25rem 0 0;
  padding: 0;
  list-style: none;
  display: grid;
  gap: 0.625rem;
}

@media (min-width: 640px) {
  .offerings-list {
    grid-template-columns: repeat(2, 1fr);
  }
}

.offerings-list li {
  font-size: 1rem;
  color: var(--color-text-secondary);
  padding-left: 1.25rem;
  position: relative;
}

.offerings-list li::before {
  content: '';
  position: absolute;
  left: 0;
  top: 0.55em;
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: var(--color-accent);
}
</style>
