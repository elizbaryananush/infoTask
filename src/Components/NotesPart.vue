<script></script>

<template>
  <div class="notes">
    <button class="plus">+</button>
    <div class="note">
      <p class="title">Hello!</p>
      <p class="context">Lorem ipsum dolor sit amet consec...</p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.notes {
  grid-column: 3/4;
  grid-row: 1 / 2;
  position: relative;

  button {
    position: absolute;
    bottom: 30px;
    right: 30px;
    width: 60px;
    height: 60px;
    border: none;
    border-radius: 50%;
    background-color: rgba(187, 255, 208, 0.6);
    display: flex;
    justify-content: center;
    align-items: center;
    font-weight: 300;
    font-size: 50px;
    box-shadow: rgba(0, 0, 0, 0.2) 0px 7px 29px 0px;
    cursor: pointer;

    &:hover {
      transform: scale(1.02);
      background-color: rgba(200, 255, 217, 0.8);
    }

    &:active {
      transform: scale(1.01);
      background-color: rgba(200, 255, 217, 0.7);
    }
  }

  .note {
    width: 100%;
    height: 100px;
    background-color: rgba(0, 0, 0, 0.3);
    padding: 15px;
    border-radius: 10px;
    border: 1px solid rgba(255, 255, 255, 0.4);
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    color: white;
    cursor: pointer;

    .title {
      font-size: 22px;
      font-weight: 500;
    }

    .context {
      font-size: 14px;
      font-weight: 200;
      opacity: 0.6;
    }

    &:hover {
      transform: scale(1.02);
    }

    &:active {
      transform: scale(1.01);
    }
  }
}
</style>