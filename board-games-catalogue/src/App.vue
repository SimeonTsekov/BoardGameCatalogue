<template>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
  <div id="app">
    <h1>Board Games Catalogue</h1>

    <div
      v-if="showForm"
      class="popover-overlay"
      @click.self="toggleForm"
    >
      <div class="popover-content">
        <AddBoardGameForm @add-game="addGame" />
        <button class="close-button" @click="toggleForm">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 384 512">
            <path d="M342.6 150.6c12.5-12.5 12.5-32.8 0-45.3s-32.8-12.5-45.3 0L192 210.7 86.6 105.4c-12.5-12.5-32.8-12.5-45.3 0s-12.5 32.8 0 45.3L146.7 256 41.4 361.4c-12.5 12.5-12.5 32.8 0 45.3s32.8 12.5 45.3 0L192 301.3 297.4 406.6c12.5 12.5 32.8 12.5 45.3 0s12.5-32.8 0-45.3L237.3 256 342.6 150.6z"/>
          </svg>
        </button>
      </div>
    </div>

    <BoardGamesList :games="games" @add-game="toggleForm" @remove-game="removeGame" />
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
      new BoardGame("Brass: Birmingham", "https://cf.geekdo-images.com/x3zxjr-Vw5iU4yDPg70Jgw__imagepagezoom/img/7a0LOL48K-7JNIOSGtcsNsIxkN0=/fit-in/1200x900/filters:no_upscale():strip_icc()/pic3490053.jpg", "Brass: Birmingham is an economic strategy game sequel to Martin Wallace's 2007 masterpiece, Brass. Brass: Birmingham tells the story of competing entrepreneurs in Birmingham during the industrial revolution between the years of 1770 and 1870."),
      new BoardGame("Here To Slay", "https://cf.geekdo-images.com/ozUv3be9fcf28tJk30bNow__imagepagezoom/img/1RalY5SJK46jPawgY1KJtEHQTpo=/fit-in/1200x900/filters:no_upscale():strip_icc()/pic5181432.jpg", "Here to Slay is a competitive role-playing fantasy strategy card game that's all about assembling a party of Heroes and slaying monsters (and sometimes sabotaging your friends too) from the creators of Unstable Unicorns."),
      new BoardGame("Furnace", "https://cf.geekdo-images.com/7UK6bLlP0Cz3EFYCqhtcSw__itemrep/img/sBBqwZDhiH4fyBRK5-LPxuX2JfQ=/fit-in/246x300/filters:strip_icc()/pic5934958.png", "Furnace is an engine-building Eurogame in which players take on the roles of 19th-century capitalists building their industrial corporations and aspiring to make as much money as they can by purchasing companies, extracting resources, and processing them in the best combinations possible.")
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
