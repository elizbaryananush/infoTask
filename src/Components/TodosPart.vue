<script>
</script>

<template>
  <div class="todos">
    <h6>To do</h6>
    <form>
      <input type="text" placeholder="Hmmm..." />
      <button>Add</button>
    </form>
    <ul>
      <li>
        <input type="checkbox" />
        <label>Wake Up in 6:00 AM</label>
      </li>
      <li>
        <input type="checkbox" />
        <label>Breakfast</label>
      </li>
    </ul>
  </div>
</template>

<style lang="scss" scoped>
.todos {
  grid-column: 2 / 3;
  background-color: white;
  background-color: rgba(0, 0, 0, 0.3);
  height: 300px;
  display: flex;
  flex-direction: column;
  gap: 10px;

  form {
    width: 100%;
    display: flex;
    align-items: center;

    input {
      width: 100%;
      height: 50px;
      background-color: rgba(0, 0, 0, 0.3);
      outline: none;
      border: none;
      color: white;
      padding: 10px;
      border-radius: 10px 0 0 10px;

      &::placeholder {
        color: white;
      }
    }

    button {
      width: 90px;
      height: 50px;
      border-radius: 0 10px 10px 0;
      border: none;
      background-color: rgba(187, 255, 208, 0.6);
      font-size: 14px;
      font-weight: 500;
      cursor: pointer;
    }
  }

  ul {
    display: flex;
    flex-direction: column;
    gap: 20px;
    padding: 10px;

    li {
      height: 30px;
      width: 100%;
      display: flex;
      align-items: center;
      gap: 10px;
      color: white;

      input{
        background-color: red;
      }
    }
  }
}
</style>