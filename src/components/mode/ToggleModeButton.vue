<template>
  <button @click="toggleDark" class="bg-bg text-text w-full flex justify-center items-center gap-4">
    <img :src="getModeIcon()" class="w-6 h-6 shrink-0" :class="invertDarkModeIcon()">
    <span class="leading-none justify-self-center"> {{ text }} </span>
    <img :src="getModeIcon()" class="w-6 h-6 shrink-0" :class="invertDarkModeIcon()">
  </button>

</template>

<script setup lang="ts">
import { useColorMode } from '@vueuse/core';

defineProps<{
  text?: string
}>()

const mode = useColorMode()
const toggleDark = () => {
  mode.value = mode.value === 'dark' ? 'light' : 'dark'
  console.log('mode.value', mode.value)
}

const getModeIcon = () => {
  return mode.value === 'dark' ? '/mdi/weather-night.svg' : '/mdi/weather-sunny.svg'
}

const invertDarkModeIcon = () => {
  return mode.value === 'dark' ? 'invert' : ''
}
</script>
