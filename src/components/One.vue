<script lang="ts" setup>
import { ref } from 'vue'
import { gsap } from 'gsap'

const words = ref('You should hover over me.')

function activate(event: MouseEvent) {
	const target = event.target as HTMLElement

	gsap.to(target, {
		scale: 1.5,
		color: 'red',
		duration: 0.3,
		ease: 'power1.out',
	})
	gsap.to(target, {
		scale: 1,
		color: 'white',
		duration: 0.3,
		ease: 'power1.out',
		delay: 0.3,
	})
}
</script>

<template>
  <h2>
    <span
      v-for="char, index in words"
      @mouseover="activate"
      :key="index"
      :class="{ space: char === ' ' }"
      class="char"
    >
      {{ char }}
    </span>
  </h2>
</template>

<style scoped>
.char {
  display: inline-block;
}

.space {
  margin-right: 1rem;
}
</style>