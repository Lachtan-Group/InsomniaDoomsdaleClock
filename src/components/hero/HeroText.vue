<template>
  <p class="text-5xl w-1/3 font-bold text-text text-center"> {{ title }}</p>
</template>

<script setup lang="ts">
defineProps<{
  title: string
}>()
</script>
