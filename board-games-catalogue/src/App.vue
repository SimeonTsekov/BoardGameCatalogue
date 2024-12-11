<template>
  <div id="app">
    <h1>Board Games Catalogue</h1>

    <button @click="toggleForm">
      {{ showForm ? "Close Form" : "Add New Board Game" }}
    </button>

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

    <BoardGamesList v-if="games.length" :games="games" />
    <p v-else>No games added yet!</p>
  </div>
</template>

<script>
import "./styles/app.css";
import "./styles/popover.css";
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
      games: [],
    };
  },
  methods: {
    toggleForm() {
      this.showForm = !this.showForm;
    },
    addGame(newGame) {
      this.games.push(newGame);
      this.showForm = false;
    },
  },
};
</script>
