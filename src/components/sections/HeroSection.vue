<script setup lang="ts">
import { useScrollTo } from '@/composables/useScrollTo'

const { scrollToId } = useScrollTo()
</script>

<template>
  <section id="hero" class="hero section">
    <div class="hero-inner section-inner">
      <p class="hero-eyebrow">Tehnoloogia & töökorraldus</p>
      <h1 class="hero-title">
        Aitame väiksematel organisatsioonidel saada tehnoloogia päriselt enda kasuks tööle.
      </h1>
      <p class="hero-subtitle">
        Aitame märgata kohti, kus aeg kaob, info jääb peitu ja töö muutub keerulisemaks kui vaja.
      </p>
      <p class="hero-message">
        Eesmärk ei ole müüa keerulist IT-d. Eesmärk on säästa aega, vähendada segadust ja toetada
        päris tööd.
      </p>
      <div class="hero-actions">
        <button type="button" class="btn btn-primary" @click="scrollToId('kontakt')">
          Räägime teie olukorrast
        </button>
        <button type="button" class="btn btn-secondary" @click="scrollToId('probleemid')">
          Vaata tüüpilisi probleeme
        </button>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  padding-top: clamp(2rem, 8vw, 6rem);
  padding-bottom: clamp(3rem, 10vw, 7rem);
  text-align: center;
}

@media (max-width: 767px) {
  .hero {
    text-align: left;
  }

  .hero-inner {
    align-items: stretch;
  }
}

.hero-inner {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.hero-eyebrow {
  font-size: 0.875rem;
  font-weight: 500;
  color: var(--color-accent);
  margin-bottom: 1.25rem;
}

.hero-title {
  font-size: clamp(1.75rem, 6vw, 3.5rem);
  font-weight: 600;
  letter-spacing: -0.04em;
  line-height: 1.12;
  text-wrap: balance;
}

@media (min-width: 768px) {
  .hero-title {
    max-width: 18ch;
    margin-left: auto;
    margin-right: auto;
  }
}

.hero-subtitle {
  margin-top: 1.25rem;
  font-size: clamp(1.0625rem, 2.5vw, 1.5rem);
  line-height: 1.45;
  color: var(--color-text-secondary);
  max-width: 36rem;
}

@media (max-width: 767px) {
  .hero-subtitle,
  .hero-message {
    max-width: none;
  }
}

.hero-message {
  margin-top: 1rem;
  font-size: 1rem;
  color: var(--color-text-tertiary);
  max-width: 32rem;
  line-height: 1.5;
}

.hero-actions {
  margin-top: 2rem;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  width: 100%;
  max-width: 24rem;
}

@media (min-width: 480px) {
  .hero-actions {
    flex-direction: row;
    flex-wrap: wrap;
    max-width: none;
    justify-content: center;
  }
}

@media (max-width: 767px) {
  .hero-actions {
    max-width: none;
  }
}

.btn {
  font-size: 1.0625rem;
  font-weight: 500;
  padding: 0.875rem 1.5rem;
  min-height: var(--touch-min);
  border-radius: var(--radius-md);
  border: none;
  cursor: pointer;
  width: 100%;
  transition: background 0.2s, color 0.2s, box-shadow 0.2s;
}

@media (min-width: 480px) {
  .btn {
    width: auto;
    border-radius: 980px;
  }
}

.btn-primary {
  color: #fff;
  background: var(--color-accent);
}

.btn-primary:hover {
  background: var(--color-accent-hover);
}

.btn-secondary {
  color: var(--color-accent);
  background: transparent;
  box-shadow: inset 0 0 0 1px var(--color-accent);
}

.btn-secondary:hover {
  background: rgba(0, 102, 204, 0.06);
}
</style>
