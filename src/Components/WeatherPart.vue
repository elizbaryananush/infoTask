<script setup>
import { ref, onMounted, watchEffect } from "vue";

const weatherData = ref();
const sunrise = ref();
const sunset = ref();

// let time = `${hours}:${minutes}`;

const getLocation = () => {
  if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(getData, handleError);
  } else {
    alert("Geolocation is not supported by this browser.");
  }
};
const getData = async (position) => {
  const { latitude, longitude } = position.coords;
  const API_key = "55e3ecc17e62952f5242fb2dc248cb36";
  const response = await fetch(
    `https://api.openweathermap.org/data/2.5/weather?lat=${latitude}&lon=${longitude}&appid=${API_key}`,
    {
      method: "GET",
      headers: {
        accept: "aplication/json",
      },
    }
  );

  const data = await response.json();

  weatherData.value = data;

  let date1 = new Date(data.sys.sunrise * 1000);

  let hours1 = date1.getHours().toString().padStart(2, "0");
  let minutes1 = date1.getMinutes().toString().padStart(2, "0");

  sunrise.value = `${hours1}:${minutes1}`;

  let date2 = new Date(data.sys.sunset * 1000);

let hours2 = date2.getHours().toString().padStart(2, "0");
let minutes2 = date2.getMinutes().toString().padStart(2, "0");

sunset.value = `${hours2}:${minutes2}`;
};

const handleError = () => {
  alert("error");
};

onMounted(() => {
  getLocation();
});

watchEffect(() => {
  console.log(weatherData.value);
});
</script>

<template>
  <div v-if="weatherData" class="weather">
    <h6>Weather</h6>
    <p>{{ Math.round(weatherData.main.temp - 273.15) }}°C</p>
    <div class="items">
      <div class="item">
        <p>Feels like</p>
        <p>{{ Math.round(weatherData.main.feels_like - 273.15) }}°C</p>
      </div>
      <div class="item">
        <p>Sunrise</p>
        <p>{{ sunrise }} AM</p>
      </div>
      <div class="item">
        <p>Sunset</p>
        <p>{{ sunset }} PM</p>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.weather {
  grid-column: 1 / 2;
  grid-row: span 3;
  background-color: rgba(0, 0, 0, 0.3);
  border: 1px rgba(255, 255, 255, 0.5) solid;
  backdrop-filter: blur(5px);
  border-radius: 20px;
  padding: 20px;

  & > p {
    font-size: 66px;
    font-weight: 600;
    color: white;
  }

  .items {
    height: 100%;
    width: 100%;

    .item {
      width: 100%;
      height: 60px;
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      align-items: center;
      color: white;
      font-size: 22px;

      p:nth-child(2) {
        background-color: rgba(255, 255, 255, 0.2);
        padding: 5px;
        border-radius: 5px;
      }
    }
  }
}
</style>