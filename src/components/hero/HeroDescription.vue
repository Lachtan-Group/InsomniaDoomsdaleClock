<template>
  <p class="text-text-subtle text-lg text-center font-bold md:w-1/3 sm:w-[75%]"> {{ text }} </p>
</template>

<script setup lang="ts">
defineProps<{
  text: string
}>()
</script>
