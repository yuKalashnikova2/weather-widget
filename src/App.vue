<script>
import CardWeather from './components/CardWeather.vue'
import Loader from './components/Loader.vue'
const API_KEY = 'f536e1ca42c2bff4d16aaae204679730'

export default {
  components: {
    CardWeather,
    Loader
  },
  data() {
    return {
      dataWeather: null,
      error: '',
      latitude: '1',
      longitude: '2',
    }
  },
  methods: {
    setCoords(lat, lon) {
      this.latitude = lat
      this.longitude = lon
    },
    getCoords() {
      navigator.geolocation.getCurrentPosition((position) => {
        let { latitude, longitude } = position.coords
        this.setCoords(latitude, longitude)

        this.getWeatherData(this.latitude, this.longitude)
      })
    },

    async getWeatherData(latitude, longitude) {
      const res = await fetch(
        `https://api.openweathermap.org/data/2.5/weather?lat=${latitude}&lon=${longitude}&units=metric&appid=${API_KEY}`
      )
      const data = await res.json()
      this.dataWeather = data
    },
  },

  mounted() {
    this.getCoords()
  },
}
</script>

<template>
  <div class="container">
    <h1>Weather Widget Design</h1>
    <div class="container__true">
      <div><span>iamswapnil </span> | <span>UI Designer</span></div>

      <div class="container__card">
        <Loader v-if="dataWeather === null" />
        <CardWeather v-else :dataWeather="dataWeather" />
      </div>
  
    </div>
  </div>
</template>

<style lang="scss" scoped>
.container {
  padding: 70px 77px;
  margin: auto;
  height: 100vh;
  h1 {
    color: #322f2f;
    font-size: 48px;
    font-weight: 700;
    margin-bottom: 18px;
  }
  span {
    color: #5f5757;
    font-size: 24px;
    font-weight: 400;
  }
  &__true {
    display: flex;
    justify-content: space-between;
  }
  &__card {
    margin: 0 auto;
  }
}
</style>
