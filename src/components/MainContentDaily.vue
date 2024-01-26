<template>
  <main class="main">
    <section class="daily">
      <div class="container daily__content">
        <div class="daily__content-btns">
          <button class="daily__content-btn1">На неделю</button>
          <button class="daily__content-btn2">Отменить</button>
        </div>
        <div class="daily__weatherBlock">
          <MainContentDailyCard
            v-for="(day, i) in dailyWeatherData"
            :key="i"
            :day="day"
            :index="i"
          />
        </div>
      </div>
    </section>
  </main>
</template>

<script>
import MainContentDailyCard from "@/components/MainContentDailyCard.vue";
import { mapActions, mapGetters } from "vuex";

export default {
  components: {
    MainContentDailyCard,
  },
  methods: {
    ...mapActions(["getWeatherData"]),
  },
  computed: {
    ...mapGetters(["dailyWeatherData"]),
  },
};
</script>

<style>
.daily__content {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.daily__content-btns {
  display: flex;
  width: 100%;
  justify-content: space-between;
}

.daily__content-btn1 {
  color: #fff;
  font-family: Montserrat;
  font-size: 18px;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
  border-radius: 5px;
  background: #4793ff;
  box-shadow: 2px 5px 25px -3px rgba(180, 180, 180, 0.25);
  padding: 8px 20px;
  border: none;
  outline: none;
}

.daily__content-btn2 {
  color: #000;
  font-family: Montserrat;
  font-size: 18px;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
  border-radius: 5px;
  background: #fff;
  box-shadow: 2px 5px 25px -3px rgba(180, 180, 180, 0.25);
  padding: 8px 20px;
  border: none;
  outline: none;
}

.daily__weatherBlock {
  border-radius: 0px 0px 20px 20px;
  background: #fff;
  box-shadow: 2px 5px 25px -3px rgba(180, 180, 180, 0.25);
  width: 100%;
  height: 240px;
  margin-top: 10px;
  padding: 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>