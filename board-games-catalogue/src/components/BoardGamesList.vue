<template>
  <div class="topnav">
    <button @click="addGame">
      <i class="fa fa-plus"></i>
    </button>
    <div class="search-bar">
      <button  >
        <i class="fa fa-search"></i>
      </button>
      <input
        type="text"
        v-model="searchQuery"
        placeholder="Search games..."
      />
    </div>
  </div>
  <div class="board-games-list">
    <ul v-if="filteredGamesList.length">
      <li v-for="(game, index) in filteredGamesList" :key="index">
        <BoardGameCard :game="game" @delete-game="deleteGame(game)" />
      </li>
    </ul>
    <p v-else>No games found!</p>
  </div>
</template>

<script>
import { defineComponent, ref, computed } from "vue";
import "@/assets/board-games-list.css";
import BoardGameCard from "@/components/BoardGameCard.vue";

export default defineComponent({
  name: "BoardGamesList",
  props: {
    games: {
      type: Array,
      required: true,
    },
  },
  components: {
    BoardGameCard,
  },
  emits: [
    "add-game",
    "remove-game"
  ],
  setup(props, { emit }) {
    const searchQuery = ref("");

    const filteredGamesList = computed(() => {
      return props.games.filter((game) => {
        return game.name.toLowerCase().includes(searchQuery.value.toLowerCase())
      })
    });

    const addGame = () => {
      emit("add-game")
    }

    const deleteGame = (gameObject) => {
      emit("remove-game", gameObject);
    };

    return {
      searchQuery,
      filteredGamesList,
      addGame,
      deleteGame
    };
  },
});
</script>
