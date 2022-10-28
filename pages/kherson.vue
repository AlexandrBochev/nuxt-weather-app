<template>
  <div class="w-full">
    <h1 class="mb-2"><b>{{region}}</b></h1>
    <hr class="mb-2">
    <TheWeather :items="items"/>
  </div>
</template>

<script setup>
  const city = 'Kherson'
  const url = `https://api.openweathermap.org/data/2.5/forecast?q=${city}&appid=7393301fe29525618e91218bd70b2f42`
  const {data} = await useFetch(url)
  const region = await data.value.city.name
  const items = await data.value.list
</script>