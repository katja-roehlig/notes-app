<script>
import { ref } from "vue";
export default {
  setup() {
    let modalView = ref(false);
    const newNote = ref("");
    let notes = ref([]);

    let showModal = () => {
      modalView.value = !modalView.value;
    };

    function getRandomColor() {
      let number = Math.floor(Math.random() * 360);
      let randomColor = "hsl(" + number + " , 100%, 75%)";
      return randomColor;
    }

    const addNote = () => {
      const date = new Date();
      notes.value.push({
        id: Math.floor(Math.random() * 1000000),
        text: newNote.value,
        date: date.toLocaleString(),
        backgroundColor: getRandomColor(),
      });
      newNote.value = "";
      modalView.value = false;
    };

    /* function deleteNote(currentId) {
      console.log(notes);
      notes = notes.filter((element) => element.id !== currentId);
    }*/

    return { modalView, newNote, showModal, notes, addNote };
  },
};
</script>

<template>
  <main>
    <div class="overlay" v-if="modalView">
      <div class="modal">
        <textarea
          v-model="newNote"
          class="modal__textarea"
          name="note"
          id="note"
          cols="30"
          rows="10"
        ></textarea>
        <button class="modal__btn" @click="addNote">Add Note</button>
        <button class="modal__btn-close" @click="showModal">X</button>
      </div>
    </div>
    <div class="container">
      <header>
        <h1>Notes</h1>
        <button class="add-btn" @click="showModal">+</button>
      </header>
      <div class="container__cards">
        <div
          class="card"
          v-for="note in notes"
          :key="note.id"
          :style="{ backgroundColor: note.backgroundColor }"
        >
          <button class="card__btn-delete">X</button>
          <p class="card__text">
            {{ note.text }}
          </p>
          <p class="card__date">{{ note.date }}</p>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
* {
  box-sizing: border-box;
  margin: 0;
}
main {
  height: 100vh;
  width: 100vw;
  background-image: repeating-linear-gradient(
      transparent 0 20px,
      rgba(0, 0, 50, 0.1) 20px 21px
    ),
    repeating-linear-gradient(
      90deg,
      transparent 0 20px,
      rgba(0, 0, 50, 0.1) 20px 21px
    );
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100vw;
  min-height: 20vh;
  padding-left: 10vw;
  padding-right: 10vw;
  background-image: linear-gradient(
    rgb(195, 195, 203),
    rgba(195, 195, 203, 0.5)
  );
  box-shadow: 0px 3px 4px rgb(2, 18, 84);
  margin-bottom: 4rem;
}
h1 {
  font-weight: bold;
  font-size: 4rem;
  font-family: sans-serif;
  color: rgb(2, 18, 84);
}
.container {
  width: 100vw;
}
.add-btn {
  border: 2px solid rgb(2, 18, 84);
  padding: 0.63rem;
  width: 3.3rem;
  height: 3.3rem;
  cursor: pointer;
  background-color: white;
  border-radius: 100%;
  color: hsl(43, 74%, 39%);
  font-size: 1.5rem;
  font-weight: bold;
  box-shadow: inset 0px 0px 10px 3px rgb(2, 18, 84);
}
.add-btn:hover {
  background-color: rgb(2, 18, 84);
  color: white;
  border: 2px solid goldenrod;
  box-shadow: inset 0px 0px 10px 3px white;
}
.overlay {
  position: absolute;
  width: 100%;
  height: 100%;
  background-color: rgbs(0, 0, 0, 0.77);
  z-index: 1;
  display: flex;
  align-items: center;
  justify-content: center;
}

.container__cards {
  display: flex;
  flex-wrap: wrap;
  padding-right: 9.8vw;
  padding-left: 9.8vw;
}
.card {
  width: 14rem;
  height: 14rem;
  background-color: rgb(237, 182, 44);
  padding: 0.6rem;
  border-radius: 0.8rem;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin-right: 2rem;
  margin-bottom: 1.3rem;
  position: relative;
  box-shadow: 2px 2px 2px 2px rgb(188, 188, 188);
}
.card__text {
  padding: 1.8rem 0.6rem;
}
.card__date {
  font-size: 0.7rem;
  text-align: right;
}

.modal {
  width: 47rem;
  background-color: rgb(255, 255, 255);
  border-radius: 0.6rem;
  padding: 1.8rem;
  position: relative;
  display: flex;
  flex-direction: column;
}
.modal__btn {
  padding: 0.6rem 1.3rem;
  font-size: 1.3rem;
  width: 50%;
  background-color: hsl(189, 100%, 40%);
  color: white;
  cursor: pointer;
  margin-top: 1rem;
  border: none;
  border-radius: 10rem;
  align-self: center;
}

.modal__btn-close,
.card__btn-delete {
  position: absolute;
  top: 0;
  right: 0;
  width: 1.7rem;
  height: 1.7rem;
  background: rgb(182, 1, 1);
  border: none;
  color: white;
  border-radius: 1rem;
}
.card__btn-delete {
  top: 0.5rem;
  right: 0.5rem;
}

.modal__textarea {
  box-shadow: 2px 2px 2px 2px hsl(189, 100%, 40%);
  border: 0.5px solid rgb(0, 217, 255);
  border-radius: 0.4rem;
  padding: 1rem;
}
</style>
