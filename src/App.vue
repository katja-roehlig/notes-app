<template>
  <main>
    <!--<div class="overlay">
      <div class="modal">
        <textarea
          class="modal__textarea"
          name="note"
          id="note"
          cols="30"
          rows="10"
        ></textarea>
        <button class="modal__btn">Add Note</button>
        <button class="modal__btn-close">X</button>
      </div>
    </div>-->
    <div class="container">
      <header>
        <h1>Notes</h1>
        <button class="add-btn">+</button>
      </header>
      <div class="container__cards">
        <div class="card">
          <p class="card__text">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ea nisi
            ullam dolores labore quis perspiciatis?
          </p>
          <p class="card__date">21/12/2022</p>
        </div>
        <div class="card">
          <p class="card__text">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ea nisi
            ullam dolores labore quis perspiciatis?
          </p>
          <p class="card__date">21/12/2022</p>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
main {
  height: 100vh;
  width: 100vw;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
h1 {
  font-weight: bold;
  margin-bottom: 1.5rem;
  font-size: 4rem;
  font-family: sans-serif;
}
.add-btn {
  border: none;
  padding: 0.63rem;
  width: 3.1rem;
  height: 3.1rem;
  cursor: pointer;
  background-color: rgb(21, 20, 20);
  border-radius: 100%;
  color: white;
  font-size: 1.5rem;
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
.container {
  max-width: 62.5rem;
  padding: 0.6rem;
  margin: 0 auto;
}
.container__cards {
  display: flex;
  flex-wrap: wrap;
}
.card {
  width: 14rem;
  height: 14rem;
  background-color: rgb(237, 182, 44);
  padding: 0.6rem;
  border-radius: 0.6rem;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin-right: 2rem;
  margin-bottom: 1.3rem;
}

.card__date {
  font-size: 0.7rem;
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
  width: 100%;
  background-color: hsl(189, 100%, 40%);
  color: white;
  cursor: pointer;
  margin-top: 1rem;
  border: none;
  border-radius: 0.4rem;
}

.modal__btn-close {
  position: absolute;
  top: 0;
  right: 0;
  width: 1.7rem;
  height: 1.7rem;
  background: red;
  border: none;
  color: white;
  border-radius: 1rem;
}
.modal__textarea {
  box-shadow: 2px 2px 2px 2px hsl(189, 100%, 40%);
  border: 0.5px solid rgb(0, 217, 255);
  border-radius: 0.4rem;
}
</style>
