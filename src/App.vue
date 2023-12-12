<script>
import CardWeather from './components/CardWeather.vue'
export default {
  components: {
    CardWeather,
  },
}
</script>

<template>
  <div class="container">
    <h1>Weather Widget Design</h1>
    <div class="container__true">
      <div><span>iamswapnil </span> | <span>UI Designer</span></div>

      <div class="container__card">
        <CardWeather />
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
