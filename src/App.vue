<script>
import CardWeather from './components/CardWeather.vue'
const API_KEY = 'f536e1ca42c2bff4d16aaae204679730'

export default {
  components: {
    CardWeather,
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
      console.log('y', lat, lon, this.latitude, this.longitude)
    },
    getCoords() {
      navigator.geolocation.getCurrentPosition((position) => {
        let { latitude, longitude } = position.coords
        this.setCoords(latitude, longitude)
        //this.latitude = String(position.coords.latitude).replace('-', '')
        //this.longitude = String(position.coords.longitude)
      })
    },
 
    getWeatherData(latitude, longitude) {
      console.log('fetch', latitude, longitude)
      /*
      navigator.geolocation.getCurrentPosition(function (position) {
        console.log(
          position.coords.latitude,
          position.coords.longitude,
          position
        )
        this.latitude = String(position.coords.latitude).replace('-', '')
        this.longitude = String(position.coords.longitude)
        console.log(this.latitude, this.longitude)
      })
      */
      fetch(
        `https://api.openweathermap.org/data/2.5/weather?lat=${latitude}&lon=${longitude}&units=metric&appid=${API_KEY}`
        // `https://api.openweathermap.org/data/2.5/weather?lat=53.24&lon=98.23&units=metric&appid=${API_KEY}`
      )
        .then((res) => res.json())
        .then((data) => (this.dataWeather = data))
    },
  },
  mounted() {
    this.getCoords()
    this.getWeatherData(this.latitude, this.longitude)
  },
//  async created() {
//     this.getCoords()
//     this.getWeatherData(this.latitude, this.longitude)
//   },
}
</script>

<template>
  <div class="container">
    <h1>Weather Widget Design</h1>
    <div class="container__true">
      <div><span>iamswapnil </span> | <span>UI Designer</span></div>

      <div class="container__card">
        {{ dataWeather }}
        <CardWeather :dataWeather="dataWeather" />
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
