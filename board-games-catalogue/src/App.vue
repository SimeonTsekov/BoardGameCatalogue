<template>
  <div id="app">
    <h1>Board Games Catalogue</h1>

    <button @click="toggleForm">
      Add A Board Game
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

    <BoardGamesList :games="games" />
  </div>
</template>

<script>
import "@/assets/main.css";
import "@/assets/popover.css";
import AddBoardGameForm from "@/components/AddBoardGameForm.vue";
import BoardGamesList from "@/components/BoardGamesList.vue";

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
