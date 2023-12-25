<script>
import { format } from 'date-fns'
export default {
  data() {
    return {
      dateNow: format(new Date(), 'dd/MM'),
      dayWeek: new Date(),
      dataTemp: this.dataWeather?.main.temp,
    }
  },
  props: {
    dataWeather: {
      type: [Object, null],
      required: true,
    },
  },
  methods: {
    styleBackground(obj) {
      console.log(obj)
      if (Math.round(obj) < 7) {
        return ''
      } else if (Math.round(obj) > 15 && Math.round(obj) < 23) {
        return 'card__weather_background-red'
      } else {
        return 'card__weather_background-yellow'
      }
    },
  },
}
</script>

<template>
  <div
    :class="[
      'card__weather',
      styleBackground(Math.round(dataWeather?.main.temp)),
    ]"
  >
    <div class="card__weather-title">
      <h2 class="card__weather-title-name">
        {{ Math.round(dataWeather?.main.temp) }}°
      </h2>
      <span class="card__weather-title-city">{{
        dataWeather?.name ? dataWeather?.name : 'City undefined'
      }}</span>
    </div>
    <div class="card__weather-info">
      <div class="card__weather-info-week">
        {{ dayWeek.toLocaleString('en', { weekday: 'long' }) }}, {{ dateNow }}
      </div>

      <div class="card__weather-info-descr">
        <div>
          <span>{{ dataWeather?.weather[0].main }}</span>
          <span
            >{{ Math.round(dataWeather?.main.temp_min) }}° /
            {{ Math.round(dataWeather?.main.temp_max) }}°</span
          >
        </div>
        <div class="card__weather-info-icon">
          <img
            :src="`https://openweathermap.org/img/wn/${dataWeather?.weather[0].icon}.png`"
            :alt="dataWeather?.weather[0].icon"
          />
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
      #3382dc -4.18%,
      #0faef8 -4.17%,
      rgba(123, 161, 222, 0.6) 110.03%
    ),
    url('https://media.istockphoto.com/id/1474651053/ru/%D1%84%D0%BE%D1%82%D0%BE/%D0%BC%D0%BE%D1%81%D0%BA%D0%BE%D0%B2%D1%81%D0%BA%D0%B8%D0%B9-%D0%B3%D0%BE%D1%80%D0%B8%D0%B7%D0%BE%D0%BD%D1%82-%D1%81-%D1%81%D0%BE%D0%B1%D0%BE%D1%80%D0%BE%D0%BC-%D0%B2%D0%B0%D1%81%D0%B8%D0%BB%D0%B8%D1%8F-%D0%B1%D0%BB%D0%B0%D0%B6%D0%B5%D0%BD%D0%BD%D0%BE%D0%B3%D0%BE-%D0%B8-%D1%81%D0%BF%D0%B0%D1%81%D1%81%D0%BA%D0%BE%D0%B9-%D0%B1%D0%B0%D1%88%D0%BD%D0%B5%D0%B9-%D0%BD%D0%B0-%D0%BA%D1%80%D0%B0%D1%81%D0%BD%D0%BE%D0%B9-%D0%BF%D0%BB%D0%BE%D1%89%D0%B0%D0%B4%D0%B8-%D1%80%D0%BE%D1%81%D1%81%D0%B8%D1%8F.jpg?s=612x612&w=0&k=20&c=Aimnt9ZMCnVqGNcYacApcBpDeV-vA_rEphHZB64dcc8='),
    lightgray 50% / cover no-repeat;
  box-shadow: 0px 8px 16px 0px rgba(0, 0, 0, 0.25);
  overflow: hidden;
  &_background-red {
    background: linear-gradient(
        322deg,
        rgba(249, 57, 57, 0.2) 13.99%,
        rgba(255, 98, 98, 0.2) 104.25%
      ),
      linear-gradient(273deg, #f94545 -7%, rgba(255, 80, 80, 0.65) 102.49%),
      url('https://www.erv.ru/upload/medialibrary/587/ww7gich3fbgmb19hqv6z82r8ithpch0x/%D0%9B%D0%B5%D0%B3%D0%B5%D0%BD%D0%B4%D0%B0%D1%80%D0%BD%D1%8B%D0%B9%20%D0%9A%D0%BE%D0%BB%D0%B8%D0%B7%D0%B5%D0%B9%20%D0%BD%D0%B0%20%D0%B2%D0%BE%D1%81%D1%85%D0%BE%D0%B4%D0%B5%20%D1%81%D0%BE%D0%BB%D0%BD%D1%86%D0%B0,%20%D0%A0%D0%B8%D0%BC,%20%D0%98%D1%82%D0%B0%D0%BB%D0%B8%D1%8F.jpg'),
      lightgray -3px -19.573px / 102.469% 100% no-repeat;
  }
  &_background-yellow {
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
      url('https://www.erv.ru/upload/medialibrary/587/ww7gich3fbgmb19hqv6z82r8ithpch0x/%D0%9B%D0%B5%D0%B3%D0%B5%D0%BD%D0%B4%D0%B0%D1%80%D0%BD%D1%8B%D0%B9%20%D0%9A%D0%BE%D0%BB%D0%B8%D0%B7%D0%B5%D0%B9%20%D0%BD%D0%B0%20%D0%B2%D0%BE%D1%81%D1%85%D0%BE%D0%B4%D0%B5%20%D1%81%D0%BE%D0%BB%D0%BD%D1%86%D0%B0,%20%D0%A0%D0%B8%D0%BC,%20%D0%98%D1%82%D0%B0%D0%BB%D0%B8%D1%8F.jpg'),
      lightgray 50% / cover no-repeat;
  }
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
