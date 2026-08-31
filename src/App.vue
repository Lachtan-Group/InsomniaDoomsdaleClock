<template>
  <AppMain>
    <div class="flex flex-col gap-4 justify-center items-center bg-bg min-h-svh">
      <HeroText title="Did Mišo and Lukáš fix their sleeping schedules?" />
      <div class="flex gap-4">
        <TimeCard :time="days" timeType="days" />
        <TimeCard :time="hours" timeType="hours" />
        <TimeCard :time="minutes" timeType="minutes" />
        <TimeCard :time="seconds" timeType="seconds" />
      </div>
    </div>
    <button @click="toggleDark" class="bg-bg text-text w-full flex">toggle</button>
  </AppMain>
</template>


<script setup lang="ts">
import { useColorMode, useCountdown } from '@vueuse/core'
import { computed } from 'vue'
import TimeCard from './components/TimeCard.vue'
import HeroText from './components/hero/HeroText.vue'

const targetDate = new Date('2036-09-01T00:00:00Z')
// const targetDate = new Date(useNow().value)
const secondsUntilTarget = Math.floor((targetDate.getTime() - Date.now()) / 1000)

const countdown = useCountdown(secondsUntilTarget)

const pad = (n: number) => String(n).padStart(2, '0')

const days = computed(() => pad(Math.floor(countdown.remaining.value / 86400)))
const hours = computed(() => pad(Math.floor((countdown.remaining.value % 86400) / 3600)))
const minutes = computed(() => pad(Math.floor((countdown.remaining.value % 3600) / 60)))
const seconds = computed(() => pad(countdown.remaining.value % 60))

countdown.start()

const mode = useColorMode()
const toggleDark = () => {
  mode.value = mode.value === 'dark' ? 'light' : 'dark'
  console.log('mode.value', mode.value)
}
</script>
