<script setup>
import { ref } from "vue";

const notes = ref([
  {
    title: "Hello",
    context:
      "Lorem ipsum dolor sit amet consectetur adipisicing elit. Amet, repellendus, ad nam dolorem molestias porro, blanditiis dolor accusantium impedit repellat perferendis adipisci ipsam facere ut deleniti inventore unde eius distinctio? Illo itaque nihil ullam alias reprehenderit! Unde ipsa quibusdam veritatis assumenda eaque eos, nobis cumque officiis sit, obcaecati vero omnis.",
  },
]);

const page = ref(1);
const selectedNote = ref(null);
const selectedInputValue = ref("");
const selectedTitleValue = ref("");
const newInputValue = ref("");
const newTitleValue = ref("");

const openNote = (note) => {
  page.value = 2;
  selectedNote.value = note;
  selectedInputValue.value = note.context;
  selectedTitleValue.value = note.title;
};

const close = () => {
  if (selectedNote.value) {
    const index = notes.value.findIndex(
      (note) => note.title === selectedNote.value.title
    );
    if (index !== -1) {
      notes.value[index].context = selectedInputValue.value;
      notes.value[index].title = selectedTitleValue.value;
    }
  }
  page.value = 1;
};

const neww = () => {
  page.value = 3;
}

const addNewNote = () => {
  notes.value.push({
    title: newTitleValue.value,
    context: newInputValue.value
  });
  newTitleValue.value = '';
  newInputValue.value = '';
  page.value = 1;
}
</script>

<template>
  <div class="notes">
    <h6>Notes</h6>
    <button @click="neww" v-if="page === 1" class="plus">+</button>
    <button @click="close" v-else-if="page === 2" class="cross">&#215;</button>
    <button @click="addNewNote" v-else-if="page === 3" class="new">{{ `<` }}</button>
    <div v-if="page === 1" class="bottom">
      <div
        @click="openNote(note)"
        v-for="note in notes"
        :key="note.title"
        class="note"
      >
        <p class="title">{{ note.title }}</p>
        <p class="context">{{ note.context.slice(0, 40) }}...</p>
      </div>
    </div>
    <div v-else-if="page === 2" class="selectedNote">
      <textarea class="title" v-model="selectedTitleValue"></textarea>
      <textarea class="context" v-model="selectedInputValue"></textarea>
    </div>
    <div v-else-if="page === 3" class="newNote">
      <textarea placeholder="Title" class="title" v-model="newTitleValue"></textarea>
      <textarea placeholder="Context" class="context" v-model="newInputValue"></textarea>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.notes {
  grid-column: 3/4;
  grid-row: span 4;
  position: relative;

  h6 {
    margin-bottom: 10px;
  }

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

  .selectedNote {
    display: flex;
    flex-direction: column;
    gap: 10px;
    color: white;
    width: 100%;
    height: 90%;

    .title {
      font-size: 26px;
      font-weight: 600;
      width: fit-content;
      height: fit-content;
      color: white;
      resize: none;
      background-color: transparent;
      border: none;
      outline: none;
    }

    .context {
      font-size: 14px;
      font-weight: 300;
      width: 100%;
      height: 100%;
      resize: none;
      background-color: transparent;
      border: none;
      outline: none;
      color: white;
    }
  }

  .newNote{
    display: flex;
    flex-direction: column;
    gap: 10px;
    color: white;
    width: 100%;
    height: 90%;

    .title {
      font-size: 26px;
      font-weight: 600;
      width: fit-content;
      height: fit-content;
      color: white;
      resize: none;
      background-color: transparent;
      border: none;
      outline: none;
    }

    .context {
      font-size: 14px;
      font-weight: 300;
      width: 100%;
      height: 100%;
      resize: none;
      background-color: transparent;
      border: none;
      outline: none;
      color: white;
    }
  }

  .bottom {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  .cross {
    left: 20px;
  }
}
</style>