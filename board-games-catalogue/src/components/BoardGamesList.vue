<template>
  <SearchBar @update-quary="updateFilter" @add-game="addGame" />

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
import SearchBar from "@/components/SearchBar.vue"

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
    SearchBar
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

    const updateFilter = (newSearchQuery) => {
      searchQuery.value = newSearchQuery.value
    }

    return {
      searchQuery,
      filteredGamesList,
      addGame,
      deleteGame,
      updateFilter
    };
  },
});
</script>
