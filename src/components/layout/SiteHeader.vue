<script setup lang="ts">
import { ref, watch, onUnmounted } from 'vue'
import { useScrollTo } from '@/composables/useScrollTo'

const { scrollToId } = useScrollTo()
const menuOpen = ref(false)

const navItems = [
  { label: 'Probleemid', id: 'probleemid' },
  { label: 'Teenused', id: 'teenused' },
  { label: 'Kontakt', id: 'kontakt' },
]

function navigate(id: string) {
  scrollToId(id)
  menuOpen.value = false
}

function toggleMenu() {
  menuOpen.value = !menuOpen.value
}

watch(menuOpen, (open) => {
  document.body.style.overflow = open ? 'hidden' : ''
})

onUnmounted(() => {
  document.body.style.overflow = ''
})
</script>

<template>
  <header class="header">
    <div class="header-inner">
      <button type="button" class="logo" @click="navigate('hero')">ArtInvest</button>

      <nav class="nav nav-desktop" aria-label="Peamine navigatsioon">
        <button
          v-for="item in navItems"
          :key="item.id"
          type="button"
          class="nav-link"
          @click="navigate(item.id)"
        >
          {{ item.label }}
        </button>
      </nav>

      <div class="header-actions">
        <button type="button" class="nav-cta nav-cta-desktop" @click="navigate('kontakt')">
          Räägime
        </button>
        <button
          type="button"
          class="menu-toggle"
          :aria-expanded="menuOpen"
          aria-controls="mobile-nav"
          :aria-label="menuOpen ? 'Sulge menüü' : 'Ava menüü'"
          @click="toggleMenu"
        >
          <span class="menu-icon" :class="{ 'menu-icon--open': menuOpen }" aria-hidden="true" />
        </button>
      </div>
    </div>

    <div
      id="mobile-nav"
      class="mobile-nav"
      :class="{ 'mobile-nav--open': menuOpen }"
      :aria-hidden="!menuOpen"
    >
      <nav class="mobile-nav-inner" aria-label="Mobiilne navigatsioon">
        <button
          v-for="item in navItems"
          :key="item.id"
          type="button"
          class="mobile-nav-link"
          @click="navigate(item.id)"
        >
          {{ item.label }}
        </button>
        <button type="button" class="mobile-nav-cta" @click="navigate('kontakt')">
          Räägime teie olukorrast
        </button>
      </nav>
    </div>

    <div
      v-if="menuOpen"
      class="mobile-backdrop"
      aria-hidden="true"
      @click="menuOpen = false"
    />
  </header>
</template>

<style scoped>
.header {
  position: sticky;
  top: 0;
  z-index: 100;
  background: rgba(251, 251, 253, 0.92);
  backdrop-filter: saturate(180%) blur(20px);
  border-bottom: 1px solid var(--color-border-light);
  padding-top: env(safe-area-inset-top);
}

.header-inner {
  max-width: var(--max-width);
  margin: 0 auto;
  min-height: var(--header-height);
  padding: 0.5rem var(--section-padding-x);
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.logo {
  font-size: 1.125rem;
  font-weight: 600;
  letter-spacing: -0.02em;
  color: var(--color-text);
  background: none;
  border: none;
  cursor: pointer;
  padding: 0.5rem 0;
  margin-right: auto;
  min-height: var(--touch-min);
  display: inline-flex;
  align-items: center;
}

.header-actions {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.nav-desktop {
  display: none;
  gap: 0.25rem;
}

.nav-link {
  font-size: 0.875rem;
  color: var(--color-text-secondary);
  background: none;
  border: none;
  cursor: pointer;
  padding: 0.5rem 0.75rem;
  min-height: var(--touch-min);
  border-radius: 980px;
  transition: color 0.2s, background 0.2s;
}

.nav-link:hover {
  color: var(--color-text);
  background: var(--color-border-light);
}

.nav-cta {
  font-size: 0.875rem;
  font-weight: 500;
  color: #fff;
  background: var(--color-accent);
  border: none;
  border-radius: 980px;
  padding: 0 1.125rem;
  min-height: var(--touch-min);
  cursor: pointer;
  transition: background 0.2s;
  white-space: nowrap;
}

.nav-cta:hover {
  background: var(--color-accent-hover);
}

.nav-cta-desktop {
  display: none;
}

.menu-toggle {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: var(--touch-min);
  height: var(--touch-min);
  padding: 0;
  background: var(--color-bg);
  border: 1px solid var(--color-border-light);
  border-radius: var(--radius-md);
  cursor: pointer;
}

.menu-icon {
  display: block;
  width: 1.125rem;
  height: 2px;
  background: var(--color-text);
  border-radius: 1px;
  position: relative;
  transition: background 0.2s;
}

.menu-icon::before,
.menu-icon::after {
  content: '';
  position: absolute;
  left: 0;
  width: 100%;
  height: 2px;
  background: var(--color-text);
  border-radius: 1px;
  transition: transform 0.2s, top 0.2s;
}

.menu-icon::before {
  top: -6px;
}

.menu-icon::after {
  top: 6px;
}

.menu-icon--open {
  background: transparent;
}

.menu-icon--open::before {
  top: 0;
  transform: rotate(45deg);
}

.menu-icon--open::after {
  top: 0;
  transform: rotate(-45deg);
}

.mobile-backdrop {
  position: fixed;
  inset: 0;
  top: var(--header-height);
  background: rgba(0, 0, 0, 0.35);
  z-index: 98;
}

.mobile-nav {
  position: absolute;
  left: 0;
  right: 0;
  top: 100%;
  z-index: 99;
  background: var(--color-surface);
  border-bottom: 1px solid var(--color-border-light);
  box-shadow: var(--shadow-soft);
  max-height: 0;
  overflow: hidden;
  opacity: 0;
  transition:
    max-height 0.3s ease,
    opacity 0.2s ease;
}

.mobile-nav--open {
  max-height: min(80vh, 420px);
  opacity: 1;
  overflow-y: auto;
  -webkit-overflow-scrolling: touch;
}

.mobile-nav-inner {
  display: flex;
  flex-direction: column;
  padding: 0.5rem var(--section-padding-x) 1rem;
  gap: 0.25rem;
}

.mobile-nav-link {
  width: 100%;
  text-align: left;
  font-size: 1.0625rem;
  font-weight: 500;
  color: var(--color-text);
  background: none;
  border: none;
  border-radius: var(--radius-md);
  padding: 0.875rem 1rem;
  min-height: var(--touch-min);
  cursor: pointer;
}

.mobile-nav-link:active {
  background: var(--color-border-light);
}

.mobile-nav-cta {
  margin-top: 0.5rem;
  width: 100%;
  font-size: 1.0625rem;
  font-weight: 500;
  color: #fff;
  background: var(--color-accent);
  border: none;
  border-radius: var(--radius-md);
  padding: 0.875rem 1rem;
  min-height: var(--touch-min);
  cursor: pointer;
}

.mobile-nav-cta:active {
  background: var(--color-accent-hover);
}

@media (min-width: 768px) {
  .nav-desktop {
    display: flex;
  }

  .nav-cta-desktop {
    display: inline-flex;
    align-items: center;
    justify-content: center;
  }

  .menu-toggle,
  .mobile-nav,
  .mobile-backdrop {
    display: none;
  }
}
</style>
