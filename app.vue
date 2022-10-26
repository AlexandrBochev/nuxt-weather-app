<template>
  <div class="max-w-lg my-12 mx-auto px-4">
    <TheHeader />
    <NuxtPage />
    <p v-for="item of items" :key="item.id">Date: {{item.dt_txt.slice(0, 10)}}</p>
    <!-- <div class="flex items-start h-60 w-full">
      <div class="flex-auto h-full mr-8 bg-red-600"></div>
      <input type="date" name="Date" value="Today" class="flex-none">
    </div> -->
  </div>
</template>

<script setup>
  const city = 'odessa'
  
  const url = `https://api.openweathermap.org/data/2.5/forecast?q=${city}&appid=7393301fe29525618e91218bd70b2f42`
  const {data} = await useFetch(url)
  const items = data.value.list

</script>

