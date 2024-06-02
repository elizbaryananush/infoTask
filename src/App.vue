<script setup>
import RemindersPartVue from "./Components/TodosPart.vue";
import WeatherPartVue from "./Components/WeatherPart.vue";
import NotesPartVue from "./Components/NotesPart.vue";
import WatchPartVue from "./Components/WatchPart.vue";
import TimerPartVue from "./Components/TimerPart.vue";
import WaterPartVue from "./Components/WaterPart.vue";
import MoodPartVue from "./Components/MoodPart.vue";
import MusicPartVue from "./Components/MusicPart.vue";
</script>

<template>
  <div class="app">
    <main class="main">
      <WeatherPartVue />
      <RemindersPartVue />
      <NotesPartVue />
      <WatchPartVue />
      <TimerPartVue />
      <MoodPartVue />
      <WaterPartVue />
      <MusicPartVue />
    </main>
  </div>
</template>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap");

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: Montserrat;
  transition: 0.1s;
  scroll-behavior: smooth;
}

li{
  list-style: none !important;
}

.app {
  width: 100%;
  height: 100vh;
  position: relative;
  overflow-y: auto;
  background: url("@/assets/background.png");
  background-repeat: no-repeat;
  background-size: cover;
  padding: 80px;

  .main {
    width: 100%;
    background: linear-gradient(
      45deg,
      rgba(255, 255, 255, 0.3) 0%,
      rgba(255, 255, 255, 0.5) 100%
    );
    border-radius: 40px;
    border: 1px rgba(255, 255, 255, 0.5) solid;
    box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
    padding: 20px;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-auto-rows: minmax(100px, auto);
    gap: 20px;
    // grid-auto-rows: minmax(100px, auto);
    // grid-template-rows: auto;

    & > div {
      background-color: rgba(0, 0, 0, 0.4);
      border: 1px rgba(255, 255, 255, 0.5) solid;
      backdrop-filter: blur(5px);
      border-radius: 20px;
      padding: 20px;

      h6 {
        color: white;
        font-size: 20px;
        font-weight: 400;
      }
    }
  }
}

.app::before {
  content: '';
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-size: cover;
  background-repeat: no-repeat;
  z-index: -1;
}
</style>
