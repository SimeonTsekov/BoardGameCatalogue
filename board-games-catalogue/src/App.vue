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

    <BoardGamesList :games="games" @remove-game="removeGame" />
  </div>
</template>

<script>
import { ref } from "vue";
import "@/assets/main.css";
import "@/assets/popover.css";
import AddBoardGameForm from "@/components/AddBoardGameForm.vue";
import BoardGamesList from "@/components/BoardGamesList.vue";
import BoardGame from "@/model/BoardGame.js"

export default {
  name: "App",
  components: {
    AddBoardGameForm,
    BoardGamesList,
  },
  setup() {
    const showForm = ref(false);
    const games = ref([
      new BoardGame("Test 1", "Test 1", "Test 1 Description"),
      new BoardGame("Test 2", "Test 2", "Test 2 Description")
    ]);

    const toggleForm = () => {
      showForm.value = !showForm.value;
    };

    const addGame = (newGame) => {
      games.value.push(newGame);
      showForm.value = false;
    };

    const removeGame = (game) => {
      games.value.splice(games.value.indexOf(game), 1)
    };

    return {
      showForm,
      games,
      toggleForm,
      addGame,
      removeGame
    };
  },
};
</script>
