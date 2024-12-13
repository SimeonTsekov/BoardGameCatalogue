<template>
  <div class="add-board-game">
    <h2>Add a New Board Game</h2>
    <form @submit.prevent="submitForm">
      <div class="form-group">
        <label for="name">Name:</label>
        <input
          type="text"
          id="name"
          v-model="name"
          placeholder="Enter board game name"
          required
        />
      </div>

      <div class="form-group">
        <label for="image">Image URL:</label>
        <input
          type="text"
          id="image"
          v-model="image"
          placeholder="Enter image URL"
          required
        />
      </div>

      <div class="form-group">
        <label for="description">Description:</label>
        <textarea
          id="description"
          v-model="description"
          placeholder="Enter board game description"
          rows="4"
          required
        ></textarea>
      </div>

      <button class="add-button" type="submit">
        <i class="fa fa-plus"></i> Add New Board Game
      </button>
    </form>
  </div>
</template>

<script>
import { ref } from "vue";
import "@/assets/add-game-form.css";
import BoardGame from "@/model/BoardGame";

export default {
  name: "AddBoardGameForm",
  setup(props, { emit }) {
    const name = ref("");
    const image = ref("");
    const description = ref("");

    const submitForm = () => {
      const newGame = new BoardGame(name.value, image.value, description.value);
      emit("add-game", newGame);
      resetForm();
    };

    const resetForm = () => {
      name.value = "";
      image.value = "";
      description.value = "";
    };

    return {
      name,
      image,
      description,
      submitForm,
    };
  },
};
</script>
