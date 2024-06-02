<script setup>
import { ref } from "vue";

const name = ref("");
const page = ref(1);
const searchTracks = ref([]);
const API_key = "44756eedabe455c6348db2fdef8bcb4f";

const search = async (e) => {
  e.preventDefault();

  const response = await fetch(
    `https://ws.audioscrobbler.com/2.0/?method=track.search&track=${name.value}&api_key=${API_key}&format=json`,
    {
      method: "GET",
      headers: {
        accept: "aplication/json",
      },
    }
  );

  const data = await response.json();
  searchTracks.value = data.results.trackmatches.track;

  console.log(searchTracks.value[0]);
};
</script>

<template>
  <div class="music">
    <form class="search">
      <input placeholder="search" type="text" v-model="name" />
      <button @click="(e) => search(e)">Search</button>
    </form>
    <div v-if="page === 1" class="tracks">
      <div v-for="searchTrack in searchTracks" class="track" :key="searchTrack">
        <img :src="searchTrack.image[0]['#text']" alt="" />
        <div class="rightpart">
          <p>{{ searchTrack.name }}</p>
          <p>{{ searchTrack.artist }}</p>
        </div>
      </div>
    </div>
    <div class="poster">
        
    </div>
  </div>
</template>

<style lang="scss" scoped>
*::-webkit-scrollbar {
  display: none;
}
.music {
  grid-column: 4/4;
  grid-row-start: 4;
  grid-row-end: 8;

  .search {
    width: 100%;
    height: 50px;
    display: flex;

    input {
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.5);
      outline: none;
      border: none;
      padding: 15px;
      font-size: 18px;
      color: white;
      border-radius: 10px 0 0 10px;
    }

    button {
      background-color: rgba(200, 255, 217, 0.8);
      border-radius: 0 10px 10px 0;
      border: 0;
      outline: 0;
      width: 80px;
      font-weight: 500;
      cursor: pointer;

      &:hover {
        background-color: rgba(223, 255, 233, 0.8);
      }

      &:active {
        background-color: rgba(163, 255, 192, 0.8);
      }
    }
  }
  .tracks {
    max-height: 350px;
    overflow-y: scroll;

    .track {
      display: flex;
      align-items: center;
      width: 100%;
      background-color: rgba(0, 0, 0, 0.317);
      margin-top: 10px;
      padding: 10px;
      border-radius: 10px;

      img {
        width: 50px;
        height: 50px;
      }

      .rightpart {
        width: 100%;
        height: 100%;
        padding: 5px;
        color: white;
        overflow: hidden;
        cursor: pointer;

        p:nth-child(1){
            font-size: 16px;
            font-weight: 500;
        }

        p:nth-child(2){
            font-size: 13px;
            opacity: 0.6;
        }

        &:hover{
            color: rgba(200, 255, 217, 0.8);
        }
      }
    }
  }
}
</style>