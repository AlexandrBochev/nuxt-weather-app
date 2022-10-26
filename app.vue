<template>
  <div class="max-w-lg my-12 mx-auto px-4">
    <TheHeader />
    <NuxtPage />
    <!-- <div class="flex items-start h-60 w-full">
      <div class="flex-auto h-full mr-8 bg-red-600"></div>
      <input type="date" name="Date" value="Today" class="flex-none">
    </div> -->
  </div>
</template>

<script setup>
  // getRegion('Kyiv')
  // async function getRegion(x) {
  //   const region = x
  //   const url = `https://api.openweathermap.org/data/2.5/forecast?q=${region}&appid=7393301fe29525618e91218bd70b2f42`
  //   const {data} = await useFetch(url)
  //   console.log(region)
  //   console.log(data.value)
  //   console.log('Data: ', data.value.city.name)
  // }
</script>

