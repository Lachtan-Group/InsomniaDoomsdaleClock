<template>
  <p class="text-text-subtle text-lg text-center font-bold sm:w-1/2 max-sm:w-[75%] md:w-1/3"> {{ text }} </p>
</template>

<script setup lang="ts">
defineProps<{
  text: string
}>()
</script>
