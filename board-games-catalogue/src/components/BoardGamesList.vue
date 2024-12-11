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
  
  <style scoped>
  .board-games-list {
    margin-top: 20px;
    text-align: left;
  }
  
  ul {
    list-style-type: none;
    padding: 0;
  }
  
  li {
    margin-bottom: 15px;
  }
  </style>