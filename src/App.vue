<script setup>

import Countdown from './components/Countdown.vue'

const getDateAfter10Days = () => {
  const today = new Date();
  const nextDate = new Date(today);

  nextDate.setDate(today.getDate() + 10);
  console.log(nextDate)
  return nextDate.toDateString();

}


</script>

<template>

  <section class="flex space-x-8 h-screen justify-center items-center w-8/12 mx-auto">

    <div>
      <img class="rounded" src="https://source.unsplash.com/1400x1200/?iphone" alt="">
    </div>
    <div class="flex flex-col space-y-3">
      <h1 class="text-5xl font-bold text-orange-500">OLD IPHONE GIVEAWAY</h1>
      <p class="font-bold text-2xl">Giveaway Ends On {{ getDateAfter10Days() }}</p>
      <p class="text-gray-600">Lorem ipsum dolor sit, amet consectetur adipisicing elit. Reprehenderit molestiae cum
        libero atque ut voluptate qui consectetur aliquid incidunt voluptatem quos, dolore, non commodi quaerat aliquam
        eligendi, quisquam totam blanditiis.</p>
      <Countdown></Countdown>
    </div>

  </section>
</template>

<style scoped>
</style>
