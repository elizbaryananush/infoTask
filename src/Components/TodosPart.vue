<script setup>
import { ref } from "vue";

const todos = ref([
  {
    todo: 'wake up in 9:00',
    checked: false,
  }
]);

const newTodo = ref('');

const addTodo = (e) => {
  e.preventDefault();
  todos.value.push({
    todo: newTodo.value,
    checked: false
  });
  newTodo.value = ''; // Clear the input field after adding todo
};

const deleteTodo = (todo) => {
  const index = todos.value.indexOf(todo);
  if (index !== -1) {
    todos.value.splice(index, 1);
  }
};
</script>

<template>
  <div class="todos">
    <h6>To do</h6>
    <form @submit.prevent="addTodo">
      <input type="text" placeholder="Hmmm..." v-model="newTodo"/>
      <button>Add</button>
    </form>
    <ul>
      <li v-for="todo in todos" :key="todo.todo">
        <input type="checkbox" v-model="todo.checked">
        <label>{{ todo.todo }}</label>
        <p @click="deleteTodo(todo)">&#215;</p>
      </li>
    </ul>
  </div>
</template>

<style lang="scss" scoped>
.todos {
  grid-column: 2 / 3;
  grid-row: span 2;
  max-height: 100%;
  background-color: white;
  background-color: rgba(0, 0, 0, 0.3);
  // height: 300px;
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
    overflow-y: auto;
    gap: 20px;
    padding: 10px;
    max-height: 100px;

    li {
      height: 30px;
      width: 100%;
      display: flex;
      align-items: center;
      gap: 10px;
      color: white;

      input {
        background-color: red;
      }

      p{
        cursor: pointer;
        font-size: 20px;
      }
    }
  }
}
</style>