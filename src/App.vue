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
          #{{ index + 1 }}
        </button>
        <span v-if="index !== components.length - 1">
          |
        </span>
      </template>
    </nav>
    <component :is="components[activeIndex]" />
  </main>
</template>

<style>
h2 {
  font-size: 5rem;
}

button {
  font-size: 2rem;
  padding: 0.25rem 1rem;
  border: none;
  background: none;
  cursor: pointer;

  &:focus-visible {
    outline: 1px solid white;
    border-radius: 4px;
  }

  &:hover {
    text-decoration: underline;
    text-decoration-thickness: 1px;
  }

  &.active {
    color: orange;
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
</style>