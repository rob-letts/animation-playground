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
  --accent: oklch(0.7 0.1529 84.18);
  --transition-duration: 0.2s;
  --transition-timing-function: ease;
}

h2 {
  font-size: 5rem;
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
  padding: 0.5rem;
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
