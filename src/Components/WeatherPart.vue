<script>
</script>

<template>
  <div class="weather">
    <h6>Weather</h6>
    <p>23°C</p>
    <div class="item">
      <p>Feels like</p>
      <p>19°C</p>
    </div>
    <div class="item">
      <p>Sunrise</p>
      <p>5:14 AM</p>
    </div>
    <div class="item">
      <p>Sunset</p>
      <p>8:15 PM</p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.weather {
  grid-column: 1 / 2;
  height: fit-content;
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

  .item {
    width: 100%;
    height: 80px;
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
</style>