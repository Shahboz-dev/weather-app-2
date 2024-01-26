<template>
  <div class="daily__card">
    <h4 class="card__title">
      {{ (index == 0 ? "Сегодня" : index == 1 ? 'Завтра' : getWeekDay) }}
    </h4>
    <p class="card__date">{{ getDay }} {{ getMonth }}</p>
    <img src="../assets/images/wheater 1.svg" alt="" />
    <p class="card__degree">
      {{ Math.floor(day.temp.day - 273.15) }}°
      <span>{{ Math.floor(day.temp.night - 273.15) }}°</span>
    </p>
    <p class="card__descr">{{ day.weather[0].description }}</p>
  </div>
</template>

<script>
import unix from "@/timestamp";

export default {
  data() {
    return {};
  },
  props: {
    day: Object,
    index: Number,
  },
  computed: {
    getWeekDay() {
      for (let i = 0; i < unix(this.day.dt, "weekday").length; i++) {
        if (unix(this.day.dt, "weekday")) {
          return (
            unix(this.day.dt, "weekday")[i].toUpperCase() +
            unix(this.day.dt, "weekday").substring(1)
          );
        } else {
          return unix(this.day.dt, "weekday");
        }
      }
    },
    getDay() {
      return unix(this.day.dt, "day");
    },
    getMonth() {
      for (let i = 0; i < unix(this.day.dt, "month").length; i++) {
        if (unix(this.day.dt, "month")) {
          return (
            unix(this.day.dt, "month")[i].toUpperCase() +
            unix(this.day.dt, "month").substring(1)
          );
        } else {
          return unix(this.day.dt, "month");
        }
      }
    },
  },
};
</script>

<style>
.daily__card {
  border-radius: 10px;
  background: rgba(71, 147, 255, 0.2);
  padding: 10px;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  width: 150px;
  height: 215px;
}

.card__title {
  color: #000;
  font-family: Montserrat;
  font-size: 18px;
  font-style: normal;
  font-weight: 500;
  line-height: normal;
}

.card__date {
  color: #939cb0;
  font-family: Montserrat;
  font-size: 14px;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
  margin-top: 7px;
  margin-bottom: 12px;
}

.card__degree {
  color: #000;
  font-family: Montserrat;
  font-size: 18px;
  font-style: normal;
  font-weight: 500;
  line-height: normal;
  display: flex;
  flex-direction: column;
  margin-top: 13px;
  margin-bottom: 6px;
}

.card__degree span {
  color: #939cb0;
  font-family: Montserrat;
  font-size: 13px;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
}

.card__descr {
  color: #939cb0;
  font-family: Montserrat;
  font-size: 13px;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
}
</style>