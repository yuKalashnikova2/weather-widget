<script>
export default {}
</script>

<template>
  <div class="card__weather">
    <div class="card__weather-title">
      <h2 class="card__weather-title-name">27°</h2>
      <span class="card__weather-title-city">Москва</span>
    </div>
    <div class="card__weather-info">
      <div class="card__weather-info-week">Monday, 25 may</div>

      <div class="card__weather-info-descr">
        <div>
          <span>Преимущественно облачно</span>
          <span>25° / 30°</span>
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
    url(<path-to-image>), lightgray 50% / cover no-repeat;
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
