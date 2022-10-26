<template>
  <div class="max-w-lg my-12 mx-auto px-4">
    <nav class="mb-8">
      <button v-for="city of citys" :key="city" v-on:click=getRegion(city) class="py-2 px-4 m-1 bg-blue-500 text-white font-semibold rounded-lg shadow-md hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-400 focus:ring-opacity-75">
        {{city}}
      </button>
    </nav>
    <div class="flex items-start h-60 w-full">
      <div class="flex-auto h-full mr-8 bg-red-600">

      </div>
      <input type="date" name="Date" value="Today" class="flex-none">
    </div>
  </div>
</template>

<script setup>
  const citys = ['Kyiv', 'Kharkiv', 'Lviv', 'Odessa', 'Kherson']
  getRegion('Kyiv')
  async function getRegion(x) {
    const region = x
    const url = `https://api.openweathermap.org/data/2.5/forecast?q=${region}&appid=7393301fe29525618e91218bd70b2f42`
    const {data} = await useFetch(url)
    console.log(region)
    console.log('Data: ', data.value.city.name)
  }
  

  
  
  
</script>

