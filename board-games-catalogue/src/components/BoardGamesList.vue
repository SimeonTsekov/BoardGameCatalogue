<template>
  <div>
    <input
      type="text"
      v-model="searchQuery"
      placeholder="Search games..."
    />
  </div>
  <div class="board-games-list">
    <h2>Games List</h2>
    <ul v-if="games.length">
      <li v-for="(game, index) in filteredGamesList" :key="index">
        <BoardGameCard :game="game" />
        <button @click="deleteGame(game)">Delete item</button>
      </li>
    </ul>
    <p v-else>No games added yet!</p>
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
    "delete-game"
  ],
  setup(props, { emit }) {
    const searchQuery = ref("");

    const deleteGame = (gameObject) => {
      emit("delete-game", gameObject);
    };

    const filteredGamesList = computed(() => {
      return props.games.filter((game) => {
        return game.name.toLowerCase().includes(searchQuery.value.toLowerCase())
      })
    });

    return {
      searchQuery,
      deleteGame,
      filteredGamesList
    };
  },
});
</script>
