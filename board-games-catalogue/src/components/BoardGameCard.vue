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
  import { defineComponent, toRefs } from "vue";
  import "@/assets/board-game-card.css";

  export default defineComponent({
    name: "BoardGameCard",
    props: {
      game: {
        type: Object,
        required: true,
      },
    },
    setup(props) {
      const { gameObject } = toRefs(props);

      return {
        gameObject,
      };
    },
  });
  </script>
