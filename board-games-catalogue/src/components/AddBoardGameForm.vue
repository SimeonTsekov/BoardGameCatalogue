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
          type="test"
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

      <button type="submit">Add Board Game</button>
    </form>
  </div>
</template>

<script>
import "../styles/add-game-form.css";
import BoardGame from "../model/BoardGame";

export default {
  data() {
    return {
      name: "",
      image: "",
      description: "",
    };
  },
  methods: {
    submitForm() {
      const newGame = new BoardGame(this.name, this.image, this.description);
      this.$emit("add-game", newGame);
      this.resetForm();
    },
    resetForm() {
      this.name = "";
      this.image = "";
      this.description = "";
    },
  },
};
</script>
  