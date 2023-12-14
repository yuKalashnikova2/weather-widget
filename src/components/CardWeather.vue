<script>
export default {
  data() {
    return {
      dateNow: Date.now(),
    }
  },
  props: {
    dataWeather: {
      type: [Object, null],
      required: true,
    },
  },
}
</script>

<template>
  <div class="card__weather">
    <div class="card__weather-title">
      <h2 class="card__weather-title-name">
        {{ Math.round(dataWeather?.main.temp) }}°
      </h2>
      <span class="card__weather-title-city">{{ dataWeather?.name }}</span>
    </div>
    <div class="card__weather-info">
      <div class="card__weather-info-week">Monday, 25 may</div>

      <div class="card__weather-info-descr">
        <div>
          <span>{{ dataWeather?.weather[0].main }}</span>
          <span
            >{{ Math.round(dataWeather?.main.temp_min) }}° /
            {{ Math.round(dataWeather?.main.temp_max) }}°</span
          >
        </div>
        <div class="card__weather-info-icon">
          <img src="/assets/weather/sun-weather.svg" alt="icon" />
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.card__weather {
  display: flex;
  flex-direction: column;
  width: 243px;
  height: 332px;
  border-radius: 16px;
  background: linear-gradient(
      325deg,
      rgba(239, 188, 56, 0.14) 14.05%,
      rgba(250, 186, 24, 0.2) 100%
    ),
    linear-gradient(
      271deg,
      #fdd368 -4.18%,
      #f8b70f -4.17%,
      rgba(222, 194, 123, 0.6) 110.03%
    ),
    url('https://media.istockphoto.com/id/1474651053/ru/%D1%84%D0%BE%D1%82%D0%BE/%D0%BC%D0%BE%D1%81%D0%BA%D0%BE%D0%B2%D1%81%D0%BA%D0%B8%D0%B9-%D0%B3%D0%BE%D1%80%D0%B8%D0%B7%D0%BE%D0%BD%D1%82-%D1%81-%D1%81%D0%BE%D0%B1%D0%BE%D1%80%D0%BE%D0%BC-%D0%B2%D0%B0%D1%81%D0%B8%D0%BB%D0%B8%D1%8F-%D0%B1%D0%BB%D0%B0%D0%B6%D0%B5%D0%BD%D0%BD%D0%BE%D0%B3%D0%BE-%D0%B8-%D1%81%D0%BF%D0%B0%D1%81%D1%81%D0%BA%D0%BE%D0%B9-%D0%B1%D0%B0%D1%88%D0%BD%D0%B5%D0%B9-%D0%BD%D0%B0-%D0%BA%D1%80%D0%B0%D1%81%D0%BD%D0%BE%D0%B9-%D0%BF%D0%BB%D0%BE%D1%89%D0%B0%D0%B4%D0%B8-%D1%80%D0%BE%D1%81%D1%81%D0%B8%D1%8F.jpg?s=612x612&w=0&k=20&c=Aimnt9ZMCnVqGNcYacApcBpDeV-vA_rEphHZB64dcc8='),
    lightgray 50% / cover no-repeat;
  box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.25);
  overflow: hidden;
  &-title {
    flex-grow: 1;
    margin-top: 24px;
    margin-left: 23px;
    &-name {
      color: #fff;
      font-size: 40px;
      font-weight: 600;
      letter-spacing: -0.8px;
    }
    &-city {
      color: #fff;
      font-family: Open Sans;
      font-size: 15px;
      font-weight: 700;
      letter-spacing: 1px;
      text-transform: uppercase;
    }
  }
  &-info {
    background-color: #fff;
    padding-top: 16px;
    padding-left: 16px;
    padding-right: 23px;
    padding-bottom: 17px;
    &-week {
      color: #191919;
      font-size: 15px;
      font-weight: 700;
      line-height: normal;
    }
    &-descr {
      display: flex;
      justify-content: space-between;
      color: #6b6b6b;
      font-size: 12px;
      font-weight: 700;
      line-height: normal;
      span {
        display: block;
      }
    }
  }
}
</style>
