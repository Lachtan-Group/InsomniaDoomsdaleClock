<template>
  <div class="flex flex-col items-center bg-gray-100 rounded-lg p-4 w-24 bg-bg-card">
    <span class="text-3xl font-bold">{{ time }}</span>
    <span class="text-sm text-gray-500"> {{ timeType }} </span>
  </div>
</template>

<script setup lang="ts">
defineProps<{
  time: string
  timeType: 'days' | 'hours' | 'minutes' | 'seconds'
}>()
</script>
