<template>
    <div class="board-games-list">
      <h2>Games List</h2>
      <ul v-if="games.length">
        <li v-for="(game, index) in games" :key="index">
          <BoardGameCard :game="game" />
        </li>
      </ul>
      <p v-else>No games added yet!</p>
    </div>
  </template>
  
  <script>
  import { defineComponent, toRefs } from "vue";
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
    setup(props) {
      const { games } = toRefs(props);
  
      return {
        games,
      };
    },
  });
  </script>
  