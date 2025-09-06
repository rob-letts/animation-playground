<script setup lang="ts">
import { ref } from 'vue'

import One from '@/components/One.vue'
import Two from '@/components/Two.vue'
import Three from '@/components/Three.vue'

const index = ref(0)
const components = [One, Two, Three]
</script>

<template>
  <select v-model.number="index">
    <option v-for="(_, index) in components" :key="index" :value="index">
      #{{ index + 1 }}
    </option>
  </select>

  <component :is="components[index]" />
</template>