<template>
  <div>
    <p class="text-2xl font-bold text-red-500">Countdown: {{ formattedTime }}</p>
  </div>
</template>

<script setup>
import { ref, onBeforeUnmount, computed } from 'vue';

const oneDayInMilliseconds = 24 * 60 * 60 * 1000; // milliseconds in a day
const tenDaysInMilliseconds = 10 * oneDayInMilliseconds; // milliseconds in 10 days

const currentTime = ref(new Date().getTime());
console.log(currentTime.value);
const targetTime = ref(currentTime.value + tenDaysInMilliseconds);

const countdownInterval = setInterval(() => {
  currentTime.value = new Date().getTime();
}, 1000);

const formattedTime = computed(() => {
  const timeRemaining = targetTime.value - currentTime.value;

  const seconds = Math.floor(timeRemaining / 1000) % 60;
  const minutes = Math.floor(timeRemaining / (1000 * 60)) % 60;
  const hours = Math.floor(timeRemaining / (1000 * 60 * 60)) % 24;
  const days = Math.floor(timeRemaining / (1000 * 60 * 60 * 24));

  return `${days}d ${hours}h ${minutes}m ${seconds}s`;
});

onBeforeUnmount(() => {
  clearInterval(countdownInterval);
});
</script>
