<template>
  <div id="app">
    <h1>Board Games Catalogue</h1>

    <!-- Button to toggle the form -->
    <button @click="toggleForm">
      {{ showForm ? "Close Form" : "Add New Board Game" }}
    </button>

    <!-- Popover for the form -->
    <div
      v-if="showForm"
      class="popover-overlay"
      @click.self="toggleForm"
    >
      <div class="popover-content">
        <AddBoardGameForm @add-game="addGame" />
        <button class="close-button" @click="toggleForm">X</button>
      </div>
    </div>

    <!-- List of board games -->
    <BoardGamesList v-if="games.length" :games="games" />
    <p v-else>No games added yet!</p>
  </div>
</template>

<script>
import AddBoardGameForm from "./components/AddBoardGameForm.vue";
import BoardGamesList from "./components/BoardGamesList.vue";

export default {
  components: {
    AddBoardGameForm,
    BoardGamesList,
  },
  data() {
    return {
      showForm: false,
      games: [], // Array to hold the list of board games
    };
  },
  methods: {
    toggleForm() {
      this.showForm = !this.showForm;
    },
    addGame(newGame) {
      this.games.push(newGame); // Add the new game to the list
      this.showForm = false; // Close the form after submission
    },
  },
};
</script>

<style>
/* Styling for the app */
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin: 20px;
}

button {
  background-color: #007bff;
  color: white;
  padding: 10px 15px;
  font-size: 16px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}

/* Popover styles */
.popover-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
}

.popover-content {
  background-color: white;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
  position: relative;
  max-width: 400px;
  width: 100%;
}

.close-button {
  position: absolute;
  top: 10px;
  right: 10px;
  background: none;
  border: none;
  font-size: 16px;
  cursor: pointer;
}

.close-button:hover {
  color: red;
}
</style>
