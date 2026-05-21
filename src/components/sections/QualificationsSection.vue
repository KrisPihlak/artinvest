<template>
  <section class="trust-strip" aria-label="Ettevõtte taust">
    <div class="trust-strip-inner">
      <p class="trust-strip-text">Rahvusvahelise kogemusega ettevõte</p>
    </div>
  </section>
</template>

<style scoped>
.trust-strip {
  padding: 1.5rem var(--section-padding-x);
  border-top: 1px solid var(--color-border-light);
  border-bottom: 1px solid var(--color-border-light);
  background: var(--color-surface);
}

.trust-strip-inner {
  max-width: var(--max-width);
  margin: 0 auto;
  text-align: center;
}

.trust-strip-text {
  margin: 0;
  font-size: 1rem;
  font-weight: 500;
  letter-spacing: -0.01em;
  color: var(--color-text-secondary);
}

@media (min-width: 768px) {
  .trust-strip {
    padding: 1.75rem var(--section-padding-x);
  }

  .trust-strip-text {
    font-size: 1.0625rem;
  }
}
</style>
