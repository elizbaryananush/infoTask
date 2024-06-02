<script setup>
import { ref } from "vue";

const glasses = ref([false, false, false, false]);

const drinked = (number) => {
  glasses.value[number] = !glasses.value[number];
};
</script>

<template>
  <div class="water">
    <h6>Water Tracker</h6>
    <div class="glasses">
      <div class="item">
        <div class="glass">
          <svg
            @click="drinked(0)"
            xmlns="http://www.w3.org/2000/svg"
            id="Layer_1"
            data-name="Layer 1"
            viewBox="0 0 24 24"
          >
            <path
              d="m1.111,0l1.747,21.246c.127,1.544,1.44,2.754,2.99,2.754h12.18c1.568,0,2.853-1.177,2.988-2.737L22.885,0H1.111Zm17.912,21.088c-.045.52-.474.912-.996.912H5.848c-.517,0-.954-.403-.997-.918L3.282,2h17.419l-1.678,19.088Z"
            />
          </svg>
          <svg
            v-if="glasses[0]"
            @click="drinked(0)"
            xmlns="http://www.w3.org/2000/svg"
            id="Layer_1"
            data-name="Layer 1"
            viewBox="0 0 24 24"
          >
            <path
              d="m18.027,24H5.848c-1.549,0-2.863-1.209-2.99-2.754L1.111,0h21.773l-1.869,21.263c-.136,1.56-1.42,2.737-2.988,2.737Z"
            />
          </svg>
        </div>
        <p>0.5l</p>
      </div>
      <div class="item">
        <div class="glass">
          <svg
            @click="drinked(1)"
            xmlns="http://www.w3.org/2000/svg"
            id="Layer_1"
            data-name="Layer 1"
            viewBox="0 0 24 24"
          >
            <path
              d="m1.111,0l1.747,21.246c.127,1.544,1.44,2.754,2.99,2.754h12.18c1.568,0,2.853-1.177,2.988-2.737L22.885,0H1.111Zm17.912,21.088c-.045.52-.474.912-.996.912H5.848c-.517,0-.954-.403-.997-.918L3.282,2h17.419l-1.678,19.088Z"
            />
          </svg>
          <svg
            v-if="glasses[1]"
            @click="drinked(1)"
            xmlns="http://www.w3.org/2000/svg"
            id="Layer_1"
            data-name="Layer 1"
            viewBox="0 0 24 24"
          >
            <path
              d="m18.027,24H5.848c-1.549,0-2.863-1.209-2.99-2.754L1.111,0h21.773l-1.869,21.263c-.136,1.56-1.42,2.737-2.988,2.737Z"
            />
          </svg>
        </div>
        <p>0.5l</p>
      </div>
      <div class="item">
        <div class="glass">
          <svg
            @click="drinked(2)"
            xmlns="http://www.w3.org/2000/svg"
            id="Layer_1"
            data-name="Layer 1"
            viewBox="0 0 24 24"
          >
            <path
              d="m1.111,0l1.747,21.246c.127,1.544,1.44,2.754,2.99,2.754h12.18c1.568,0,2.853-1.177,2.988-2.737L22.885,0H1.111Zm17.912,21.088c-.045.52-.474.912-.996.912H5.848c-.517,0-.954-.403-.997-.918L3.282,2h17.419l-1.678,19.088Z"
            />
          </svg>
          <svg
            v-if="glasses[2]"
            @click="drinked(2)"
            xmlns="http://www.w3.org/2000/svg"
            id="Layer_1"
            data-name="Layer 1"
            viewBox="0 0 24 24"
          >
            <path
              d="m18.027,24H5.848c-1.549,0-2.863-1.209-2.99-2.754L1.111,0h21.773l-1.869,21.263c-.136,1.56-1.42,2.737-2.988,2.737Z"
            />
          </svg>
        </div>
        <p>0.5l</p>
      </div>
      <div class="item">
        <div class="glass">
          <svg
            @click="drinked(3)"
            xmlns="http://www.w3.org/2000/svg"
            id="Layer_1"
            data-name="Layer 1"
            viewBox="0 0 24 24"
          >
            <path
              d="m1.111,0l1.747,21.246c.127,1.544,1.44,2.754,2.99,2.754h12.18c1.568,0,2.853-1.177,2.988-2.737L22.885,0H1.111Zm17.912,21.088c-.045.52-.474.912-.996.912H5.848c-.517,0-.954-.403-.997-.918L3.282,2h17.419l-1.678,19.088Z"
            />
          </svg>
          <svg
            v-if="glasses[3]"
            @click="drinked(3)"
            xmlns="http://www.w3.org/2000/svg"
            id="Layer_1"
            data-name="Layer 1"
            viewBox="0 0 24 24"
          >
            <path
              d="m18.027,24H5.848c-1.549,0-2.863-1.209-2.99-2.754L1.111,0h21.773l-1.869,21.263c-.136,1.56-1.42,2.737-2.988,2.737Z"
            />
          </svg>
        </div>
        <p>0.5l</p>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.water {
  grid-column: 2 / 4;
  grid-row: span 3;

  .glasses {
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: space-evenly;

    .item {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: space-evenly;
      gap: 20px;
      color: white;
      font-size: 16px;
      cursor: pointer;

      svg {
        width: 120px;
        height: 120px;
        fill: rgba(255, 255, 255, 0.7);
      }

      .glass {
        width: fit-content;
        height: fit-content;
        position: relative;

        svg:nth-child(2) {
          position: absolute;
          top: 0;
          left: 0;
          fill: rgba(187, 255, 208, 0.6);
          z-index: -1;
        }
      }
    }
  }
}
</style>