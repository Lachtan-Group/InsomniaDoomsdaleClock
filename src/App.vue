<template>
  <AppMain>
    <div class="flex flex-col gap-8 justify-center items-center bg-bg min-h-svh">
      <HeroText title="Did Mišo and Lukáš fix their sleeping schedules?" />
      <hr class="border-t border-text-subtle opacity-20 w-1/2">
      <TimeCardContainer class="py-4">
        <TimeCard :time="days" timeType="days" />
        <TimeCard :time="hours" timeType="hours" />
        <TimeCard :time="minutes" timeType="minutes" />
        <TimeCard :time="seconds" timeType="seconds" />
      </TimeCardContainer>
      <hr class="border-t border-text-subtle opacity-20 w-1/2">
      <HeroDescription
        text="When this countdown reaches 0 on September 1st, 2036 at 00:00 and Lukáš and Mišo still haven't fixed their sleeping schedules, they will be consider a failure!" />
    </div>
    <ToggleModeButton text="Toggle dark mode" class="pb-1" />
  </AppMain>
</template>


<script setup lang="ts">
import { useCountdown } from '@vueuse/core'
import { computed } from 'vue'
import TimeCard from './components/time/TimeCard.vue'
import HeroText from './components/hero/HeroText.vue'
import HeroDescription from './components/hero/HeroDescription.vue'
import TimeCardContainer from './components/time/TimeCardContainer.vue'
import ToggleModeButton from './components/mode/ToggleModeButton.vue'

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


</script>
