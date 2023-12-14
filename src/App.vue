<script>

// import { mounted } from 'vue'
import CardWeather from './components/CardWeather.vue'
const API_KEY = 'f536e1ca42c2bff4d16aaae204679730'
export default {
  components: {
    CardWeather,
  },
  data () {
    return {
      dataWeather: null,
    }

  },
  methods: {
    getWeatherData() {
      fetch(`https://api.openweathermap.org/data/2.5/weather?lat=44.34&lon=10.99&units=metric&appid=${API_KEY}`)
      .then(res => res.json())
      .then(data => this.dataWeather = data)
    }
  },
  mounted() {
    this.getWeatherData()
  }
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
        <CardWeather />
        <CardWeather />
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.container {
  padding: 70px 77px;
  margin: auto;
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
    display: flex;
    gap: 100px;
    flex-wrap: wrap;
  }
}
</style>
