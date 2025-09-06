<script setup lang="ts">
import { ref } from 'vue'

import One from '@/components/One.vue'
import Two from '@/components/Two.vue'
import Three from '@/components/Three.vue'

const activeIndex = ref(0)
const components = [One, Two, Three]
</script>

<template>
  <main>
    <nav>
      <template
        v-for="(_, index) in components"
        :key="index"
      >
        <button
          @click="activeIndex = index"
          :value="index"
          :class="{ active: activeIndex === index }"
        >
          <span class="hash">#</span>{{ index + 1 }}
        </button>
        <span v-if="index !== components.length - 1">
          |
        </span>
      </template>
    </nav>

    <section>
      <component :is="components[activeIndex]" />
    </section>
  </main>
</template>

<style>
:root {
  --base-color: oklch(1 0 225);
  --dim: oklch(1 0 225 / 50%);
  --accent: oklch(65.4% 0.235 34.0);
  --transition-duration: 0.2s;
  --transition-timing-function: ease;
  --heading-size: clamp(2.5rem, 5vw + 1rem, 5rem);
}

h2 {
  font-size: var(--heading-size);
}

button {
  font-size: 2rem;
  padding: 0.25rem 1rem;
  border: none;
  background: none;
  cursor: pointer;
  transition: color var(--transition-duration) var(--transition-timing-function);

  &:focus-visible {
    outline: 1px solid var(--base-color);
    border-radius: 4px;
  }

  &.active {
    color: var(--accent);
  }

  &:not(.active) .hash {
    opacity: 0.25;
  }
}

main {
  text-align: center;
  padding-top: 0.5rem;
  height: 100dvh;
  display: grid;
  grid-template-rows: auto 1fr;
}

section {
  margin: 1rem;
  display: grid;
  place-items: center;
  height: 50%;
}

nav {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 1rem;
}

.hash {
  transition: opacity var(--transition-duration) var(--transition-timing-function);
  margin-right: 0.25rem;
  color: inherit;
}
</style>