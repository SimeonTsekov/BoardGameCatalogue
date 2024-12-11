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
  export default {
    props: {
      game: {
        type: Object,
        required: true,
      },
    },
  };
  </script>
  
  <style scoped>
  .board-game-card {
    display: flex;
    align-items: flex-start;
    margin-bottom: 15px;
    border-bottom: 1px solid #ddd;
    padding-bottom: 10px;
  }
  
  .game-image {
    width: 100px;
    height: 100px;
    margin-right: 15px;
    object-fit: cover;
    border-radius: 5px;
  }
  
  h3 {
    margin: 0;
  }
  
  p {
    margin: 5px 0 0;
  }
  </style>