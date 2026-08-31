<template>
  <p class="text-3xl font-bold text-text text-center"> {{ title }}</p>
</template>

<script setup lang="ts">
defineProps<{
  title: string
}>()
</script>
