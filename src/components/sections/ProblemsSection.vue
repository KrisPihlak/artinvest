<script setup lang="ts">
const cards = [
  {
    title: 'Kui see üks inimene puudub, siis keegi ei tea, kus info asub',
    description:
      'Info elab inimeste peas. Kui üks inimene puudub, kaob koos temaga teadmine: kus failid on, mis seisus töö on või kuidas midagi tehakse.',
  },
  {
    title: 'Meil on kõik olemas, aga ülevaadet ei ole',
    description:
      'Arvutid ja programmid võivad olemas olla, kuid puudub tervikpilt, nähtav töövoog ja selge protsess.',
  },
  {
    title: 'Midagi ei ole katki, aga kõik võtab liiga kaua aega',
    description:
      'Sama infot sisestatakse mitu korda, inimesed otsivad faile ja kulutavad aega tegevustele, mida võiks teha lihtsamalt.',
  },
  {
    title: 'Tahaks asja paremaks teha, aga ei tea kust alustada',
    description:
      'Organisatsioon kasvab kiiremini kui töökorraldus — kliente ja ülesandeid tuleb juurde, kuid töö käib endiselt harjumuste järgi.',
  },
]

const deeperProblems = [
  {
    title: 'Info elab inimeste peas',
    text: 'Kui üks inimene puudub, kaob koos temaga teadmine: kus failid on, mis seisus töö on või kuidas midagi tehakse.',
  },
  {
    title: 'Kõik töötab, aga liiga aeglaselt',
    text: 'Sama infot sisestatakse mitu korda, inimesed otsivad faile, küsivad üksteiselt infot ja kulutavad aega tegevustele, mida võiks teha lihtsamalt.',
  },
  {
    title: 'Organisatsioon kasvab kiiremini kui töökorraldus',
    text: 'Kliente, objekte ja ülesandeid tuleb juurde, kuid töö käib endiselt Exceli, paberite, telefonide ja harjumuste järgi.',
  },
  {
    title: 'Tehnoloogia olemasolu ei tähenda süsteemi olemasolu',
    text: 'Arvutid ja programmid võivad olemas olla, kuid puudub tervikpilt, nähtav töövoog ja selge protsess.',
  },
]
</script>

<template>
  <section id="probleemid" class="section problems">
    <div class="section-inner">
      <span class="section-label">Tüüpilised probleemid</span>
      <h2 class="section-title">Probleemid, mida kliendid sageli ise ei märka</h2>
      <p class="section-lead">
        Need ei pruugi tunduda „katkised“, kuid iga päev võtavad nad aega ja tekitavad segadust.
      </p>

      <div class="cards-grid">
        <article v-for="card in cards" :key="card.title" class="card">
          <h3 class="card-title">{{ card.title }}</h3>
          <p class="card-text">{{ card.description }}</p>
        </article>
      </div>

      <div class="deeper-block">
        <h3 class="deeper-heading">Lähemalt</h3>
        <ul class="deeper-list">
          <li v-for="item in deeperProblems" :key="item.title" class="deeper-item">
            <strong>{{ item.title }}</strong>
            <span>{{ item.text }}</span>
          </li>
        </ul>
      </div>
    </div>
  </section>
</template>

<style scoped>
.problems {
  background: var(--color-surface);
}

.cards-grid {
  margin-top: 2rem;
  display: grid;
  gap: 1rem;
  grid-template-columns: 1fr;
}

@media (min-width: 768px) {
  .cards-grid {
    margin-top: 3rem;
    gap: 1.25rem;
  }
}

@media (min-width: 640px) {
  .cards-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

.card {
  padding: 1.25rem 1.375rem;
  background: var(--color-bg);
  border-radius: var(--radius-lg);
  border: 1px solid var(--color-border-light);
  transition: box-shadow 0.25s;
}

@media (min-width: 768px) {
  .card {
    padding: 2rem;
  }
}

.card:hover {
  box-shadow: var(--shadow-soft);
}

.card-title {
  font-size: 1.125rem;
  font-weight: 600;
  letter-spacing: -0.02em;
  line-height: 1.35;
  text-wrap: balance;
}

@media (min-width: 768px) {
  .card-title {
    font-size: 1.25rem;
  }
}

.card-text {
  margin-top: 0.75rem;
  font-size: 0.9375rem;
  color: var(--color-text-secondary);
  line-height: 1.5;
}

.deeper-block {
  margin-top: 2.5rem;
  padding-top: 2rem;
  border-top: 1px solid var(--color-border-light);
}

@media (min-width: 768px) {
  .deeper-block {
    margin-top: 4rem;
    padding-top: 3rem;
  }
}

.deeper-heading {
  font-size: 1.5rem;
  font-weight: 600;
  letter-spacing: -0.02em;
}

.deeper-list {
  margin: 1.5rem 0 0;
  padding: 0;
  list-style: none;
  display: grid;
  gap: 1.5rem;
}

@media (min-width: 768px) {
  .deeper-list {
    grid-template-columns: repeat(2, 1fr);
  }
}

.deeper-item {
  display: flex;
  flex-direction: column;
  gap: 0.375rem;
}

.deeper-item strong {
  font-size: 1rem;
  font-weight: 600;
}

.deeper-item span {
  font-size: 0.9375rem;
  color: var(--color-text-secondary);
  line-height: 1.5;
}
</style>
