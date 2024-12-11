<template>
    <div class="board-game-card">
      <img :src="game.image" :alt="game.name" class="game-image" />
      <div>
        <h3>{{ game.name }}</h3>
        <p>{{ game.description }}</p>
      </div>
    </div>
  </template>
  
  <script>
  import "../styles/board-game-card.css";
  
  export default {
    props: {
      game: {
        type: Object,
        required: true,
      },
    },
  };
  </script>