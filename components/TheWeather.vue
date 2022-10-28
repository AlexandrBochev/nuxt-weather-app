<template>
  <div class="w-full">
    <div :class="{error}" class="absolute left-0 top-0 w-full h-full invisible opacity-0 duration-300">
      <div @click="closePopup()" class="absolute left-0 top-0 w-full h-full bg-black opacity-50"></div>
      <div class="absolute left-1/2 -translate-x-1/2 w-72 bg-white rounded-md border-2 border-indigo-500/100 p-6 my-20">
        <h3 class="text-center">Please select another date.</h3>
        <button @click="closePopup()" class="relative left-1/2 -translate-x-1/2 mt-8 py-1 px-6 bg-blue-500 text-white font-semibold rounded-lg shadow-md hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-400 focus:ring-opacity-75">Close</button>
      </div>
      
    </div>
    <div class="flex items-start h-60 w-full">
      <div class="flex-auto h-full mr-8">
        <img :src="icon" alt="icon">
        <p>Temperature: <b>{{temp}}</b> °C</p>
        <p>Wind: <b>{{wind}}</b> m/s</p>
        <p>Humidity: <b>{{humidity}}</b> %</p>
      </div>
      <input type="date" v-model="date" @change="chooseDate(date)" class="flex-none" >
    </div>
  </div>
</template>

<script>
export default {
  props: ['items'],
  data() {
    return {
      error: false,
      date: '',
      icon: '',
      temp: '',
      wind: '',
      humidity: '',
    }
  },

  methods: {
    chooseDate(e) {
      let cheсk
      for (let i = 0; i < this.items.length; i++) {
        if (this.items[i].dt_txt !== `${e} 21:00:00`) {
          cheсk = false
        } else {
          this.icon = `http://openweathermap.org/img/wn/${this.items[i].weather[0].icon}@2x.png`
          this.temp = (((this.items[i].main.temp - 32) * 5/9) / 10).toFixed(2)
          this.wind = (Number(this.items[i].wind.speed) * 1.6214).toFixed(2)
          this.humidity = this.items[i].clouds.all.toFixed()
          return true
        }
      }
      this.error = true
    },
    closePopup() {
      this.error = false
      this.date = new Date().toISOString().substr(0, 10)
    },
  },

  mounted(){
    this.date = new Date().toISOString().substr(0, 10)
    
    for (let i = 0; i < this.items.length; i++) {
      if (this.items[i].dt_txt !== `${this.date} 21:00:00`) {
        this.icon = `http://openweathermap.org/img/wn/${this.items[i].weather[0].icon}@2x.png`
        this.temp = (((this.items[i].main.temp - 32) * 5/9) / 10).toFixed(2)
        this.wind = (Number(this.items[i].wind.speed) * 1.6214).toFixed(2)
        this.humidity = this.items[i].clouds.all.toFixed()
      }
    }
  }, 
}
</script>

<style>
  .error {
    visibility: visible;
    opacity: 1;
  }
</style>