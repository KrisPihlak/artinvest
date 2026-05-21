<script setup lang="ts">
const year = new Date().getFullYear()
</script>

<template>
  <footer class="footer">
    <div class="footer-inner">
      <p class="footer-brand">ArtInvest</p>
      <p class="footer-tagline">
        Aitame väiksematel organisatsioonidel saada tehnoloogia päriselt enda kasuks tööle.
      </p>
      <p class="footer-copy">© {{ year }} ArtInvest. Kõik õigused kaitstud.</p>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  padding: 2.5rem var(--section-padding-x) max(2.5rem, env(safe-area-inset-bottom, 0px));
  border-top: 1px solid var(--color-border-light);
  background: var(--color-surface);
}

@media (min-width: 768px) {
  .footer {
    padding-top: 3rem;
    padding-bottom: 4rem;
  }
}

.footer-inner {
  max-width: var(--max-width);
  margin: 0 auto;
  text-align: center;
}

.footer-brand {
  font-size: 1.125rem;
  font-weight: 600;
  letter-spacing: -0.02em;
}

.footer-tagline {
  margin-top: 0.5rem;
  font-size: 0.9375rem;
  color: var(--color-text-secondary);
  max-width: 28rem;
  margin-left: auto;
  margin-right: auto;
  line-height: 1.5;
  padding: 0 0.25rem;
}

.footer-copy {
  margin-top: 2rem;
  font-size: 0.8125rem;
  color: var(--color-text-tertiary);
}
</style>
