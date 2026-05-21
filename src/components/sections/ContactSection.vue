<script setup lang="ts">
import { ref } from 'vue'

const name = ref('')
const email = ref('')
const message = ref('')
const submitted = ref(false)

function handleSubmit() {
  submitted.value = true
  name.value = ''
  email.value = ''
  message.value = ''
}
</script>

<template>
  <section id="kontakt" class="section contact">
    <div class="section-inner contact-inner">
      <span class="section-label">Kontakt</span>
      <h2 class="section-title">Räägime teie olukorrast</h2>
      <p class="section-lead">
        Kirjeldage lühidalt oma organisatsiooni ja mida soovite paremaks — võtame ühendust ja arutame
        järgmised sammud ilma kohustuseta.
      </p>

      <form v-if="!submitted" class="contact-form" @submit.prevent="handleSubmit">
        <label class="field">
          <span class="field-label">Nimi</span>
          <input v-model="name" type="text" name="name" required autocomplete="name" />
        </label>
        <label class="field">
          <span class="field-label">E-post</span>
          <input
            v-model="email"
            type="email"
            name="email"
            required
            autocomplete="email"
          />
        </label>
        <label class="field field-full">
          <span class="field-label">Sõnum</span>
          <textarea v-model="message" name="message" rows="4" required />
        </label>
        <button type="submit" class="btn-submit">Saada sõnum</button>
      </form>

      <p v-else class="success-message" role="status">
        Täname! Sõnum on salvestatud (demo režiimis). Ühendame vormi päriselt, kui teil on
        e-posti aadress valmis.
      </p>

      <p class="contact-alt">
        Või kirjutage otse:
        <a href="mailto:kontakt@artinvest.ee">kontakt@artinvest.ee</a>
      </p>
    </div>
  </section>
</template>

<style scoped>
.contact {
  background: var(--color-surface);
}

.contact-inner {
  max-width: 560px;
}

.contact-form {
  margin-top: 2rem;
  display: grid;
  gap: 1rem;
  grid-template-columns: 1fr;
}

@media (min-width: 640px) {
  .contact-form {
    margin-top: 2.5rem;
    gap: 1.25rem;
    grid-template-columns: 1fr 1fr;
  }
}

.field {
  display: flex;
  flex-direction: column;
  gap: 0.375rem;
}

.field-full {
  grid-column: 1 / -1;
}

.field-label {
  font-size: 0.8125rem;
  font-weight: 500;
  color: var(--color-text-secondary);
}

.field input,
.field textarea {
  font-family: inherit;
  font-size: 16px;
  padding: 0.875rem 1rem;
  min-height: var(--touch-min);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-md);
  background: var(--color-bg);
  color: var(--color-text);
  width: 100%;
  transition: border-color 0.2s, box-shadow 0.2s;
}

.field textarea {
  min-height: 8rem;
}

.field input:focus,
.field textarea:focus {
  outline: none;
  border-color: var(--color-accent);
  box-shadow: 0 0 0 3px rgba(0, 102, 204, 0.15);
}

.field textarea {
  resize: vertical;
}

.btn-submit {
  grid-column: 1 / -1;
  width: 100%;
  font-size: 1.0625rem;
  font-weight: 500;
  color: #fff;
  background: var(--color-accent);
  border: none;
  border-radius: var(--radius-md);
  padding: 0.875rem 2rem;
  min-height: var(--touch-min);
  cursor: pointer;
  transition: background 0.2s;
}

@media (min-width: 640px) {
  .btn-submit {
    width: auto;
    justify-self: start;
    border-radius: 980px;
  }
}

.btn-submit:hover {
  background: var(--color-accent-hover);
}

.success-message {
  margin-top: 2rem;
  padding: 1.25rem 1.5rem;
  background: rgba(0, 102, 204, 0.08);
  border-radius: var(--radius-md);
  color: var(--color-accent);
  font-size: 0.9375rem;
}

.contact-alt {
  margin-top: 2rem;
  font-size: 0.9375rem;
  color: var(--color-text-secondary);
  line-height: 1.5;
  word-break: break-word;
}
</style>
