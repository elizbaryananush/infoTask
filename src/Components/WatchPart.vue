<script setup>
import { onMounted, ref} from "vue";

const date = ref(new Date());
const time = ref()

onMounted(() => {
  setInterval(() => {
    date.value = new Date()

if(date.value.getMinutes().lenght == 1){
  time.value = date.value.getHours() + ':' + '0' + date.value.getMinutes()
}else{
  time.value = date.value.getHours() + ':' + date.value.getMinutes()
}
  }, 1000);
});
</script>

<template>
  <div class="watch">
    <h6>Time</h6>
    <div class="time">
      <div class="inside">
        <h1>{{date.getHours() + ':' + date.getMinutes()}}</h1>
        <p>Sunday , June 2 2024</p>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.watch {
  grid-column: 4 / 4;
  grid-row: span 3;

  h6 {
    position: absolute;
  }

  .time {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;

    .inside {
      width: fit-content;
      height: fit-content;
      text-align: center;
      color: white;

      h1 {
        font-size: 90px;
        font-weight: 400;
      }

      p {
        font-size: 20px;
      }
    }
  }
}
</style>