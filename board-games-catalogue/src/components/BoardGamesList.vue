<template>
    <div class="board-games-list">
      <h2>Games List</h2>
      <ul>
        <li v-for="(game, index) in games" :key="index">
          <BoardGameCard :game="game" />
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  import "../styles/board-games-list.css";
  import BoardGameCard from "./BoardGameCard.vue";
  
  export default {
    props: {
      games: {
        type: Array,
        required: true,
      },
    },
    components: {
      BoardGameCard,
    },
  };
  </script>