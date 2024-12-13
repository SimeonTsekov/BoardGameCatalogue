<template>
  <div class="board-game-card">
    <div class="image-container">
      <img :src="game.image" :alt="game.name" />
    </div>
    <div>
      <h3>{{ game.name }}</h3>
      <p>{{ game.description }}</p>
    </div>
    <button @click="deleteGame" class="delete-button">
      <i class="fa fa-trash-o"></i>
    </button>
  </div>
</template>

<script>
import { defineComponent } from "vue";
import "@/assets/board-game-card.css";

export default defineComponent({
  name: "BoardGameCard",
  props: {
    game: {
      type: Object,
      required: true,
    },
  },
  emits: ["delete-game"],
  setup(props, { emit }) {
    const deleteGame = () => {
      emit("delete-game")
    }

    return {
      deleteGame
    };
  },
});
</script>
