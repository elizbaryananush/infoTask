<script setup>
import { ref } from "vue";

const intervalId = ref();
const inchvoraya = ref(false);
const hours = ref("00");
const minutes = ref("00");
const seconds = ref("00");

const submit = () => {
  if (
    hours.value == "00" &&
    minutes.value == "00" &&
    seconds.value < 5 &&
    seconds.value === "00" &&
    inchvoraya
  ) {
    alert("input atleast 5 seconds");
  } else {
    inchvoraya.value = !inchvoraya.value;

    if(hours.value.length == 1){
      hours.value = '0' + hours.value
    }

    if(minutes.value.length == 1){
      minutes.value = '0' + minutes.value
    }

    if(seconds.value.length == 1){
      seconds.value = '0' + seconds.value
    }

    intervalId.value = setInterval(() => {
      if (seconds.value > 0) {
        if (seconds.value > 10) {
          seconds.value--;
        } else {
          seconds.value = "0" + (seconds.value - 1);
        }
      } else {
        if (minutes.value > 0) {
          seconds.value = 59;
          minutes.value--;

          if (minutes.value > 10) {
            minutes.value--;
          } else {
            minutes.value = "0" + minutes.value;
          }
        } else {
          if (hours.value > 0) {
            seconds.value = 59;
            minutes.value = 59;
            hours.value--;

            if (hours.value > 10) {
              hours.value--;
            } else {
              hours.value = "0" + hours.value;
            }
          }
        }
      }
    }, 1000);
  }
};

const stop = () => {
  inchvoraya.value = !inchvoraya.value;
  hours.value = "00";
  minutes.value = "00";
  seconds.value = "00";
  clearInterval(intervalId.value);
};
</script>

<template>
  <div class="timer">
    <div class="top">
      <h6>Timer</h6>
      <p @click="stop">Change Goal</p>
    </div>
    <div class="content">
      <div class="bigRound">
        <div class="smallRound">
          <div v-if="inchvoraya" class="change">
            <input
              maxlength="2"
              type="number"
              v-model="hours"
              @change="(e) => (hours = e.target.value)"
              placeholder="00"
            />
            <input
              maxlength="2"
              type="number"
              v-model="minutes"
              @change="(e) => (minutes = e.target.value)"
              placeholder="00"
            />
            <input
              maxlength="2"
              type="number"
              v-model="seconds"
              @change="(e) => (seconds = e.target.value)"
              placeholder="00"
            />
          </div>
          <p v-else-if="!inchvoraya">{{ hours }}:{{ minutes }}:{{ seconds }}</p>
          <div class="play">
            <svg
              v-if="inchvoraya"
              @click="submit"
              xmlns="http://www.w3.org/2000/svg"
              id="Filled"
              viewBox="0 0 24 24"
              width="512"
              height="512"
            >
              <path
                d="M20.492,7.969,10.954.975A5,5,0,0,0,3,5.005V19a4.994,4.994,0,0,0,7.954,4.03l9.538-6.994a5,5,0,0,0,0-8.062Z"
              />
            </svg>

            <svg
              v-else
              @click="stop"
              xmlns="http://www.w3.org/2000/svg"
              id="Layer_1"
              data-name="Layer 1"
              viewBox="0 0 24 24"
              width="512"
              height="512"
            >
              <path
                d="m12,0C5.383,0,0,5.383,0,12s5.383,12,12,12,12-5.383,12-12S18.617,0,12,0Zm0,22c-5.514,0-10-4.486-10-10S6.486,2,12,2s10,4.486,10,10-4.486,10-10,10Zm2-15h-4c-1.654,0-3,1.346-3,3v4c0,1.654,1.346,3,3,3h4c1.654,0,3-1.346,3-3v-4c0-1.654-1.346-3-3-3Zm1,7c0,.551-.449,1-1,1h-4c-.551,0-1-.449-1-1v-4c0-.551.449-1,1-1h4c.551,0,1,.449,1,1v4Z"
              />
            </svg>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
input::-webkit-inner-spin-button,
input::-webkit-outer-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

.timer {
  grid-column: 1/2;
  grid-row: span 4;

  .top {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    color: white;

    p {
      cursor: pointer;

      &:hover {
        text-decoration: underline;
      }
    }
  }

  .content {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;

    .bigRound {
      width: 200px;
      height: 200px;
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      background-color: rgba(187, 255, 208, 0.6);

      .smallRound {
        width: 185px;
        height: 185px;
        border-radius: 50%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        background-color: white;
        position: relative;

        .change {
          display: flex;
          gap: 10px;

          input {
            width: 40px;
            height: 30px;
            padding: 6px;
            border: none;
            border-bottom: rgb(166, 209, 179) 2px solid;
            outline: none;
            font-size: 18px;
          }
        }

        .play {
          position: absolute;
          bottom: 20px;
          svg {
            width: 30px;
            height: 30px;
            fill: rgb(166, 209, 179);
            cursor: pointer;

            &:hover {
              transform: scale(1.05);
              fill: rgb(172, 225, 188);
            }

            &:active {
              transform: scale(1);
            }
          }
        }

        p {
          font-size: 20px;
        }
      }
    }
  }
}
</style>