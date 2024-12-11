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
  
  <style scoped>
  .add-board-game {
    margin: auto;
    padding: 20px;
    border: 1px solid #ddd;
    border-radius: 5px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
  
  .form-group {
    margin-bottom: 15px;
  }
  
  label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
  }
  
  input,
  textarea {
    width: 100%;
    padding: 8px;
    margin-bottom: 5px;
    border: 1px solid #ccc;
    border-radius: 4px;
    font-size: 16px;
  }
  
  button {
    background-color: #4CAF50;
    color: white;
    padding: 10px 15px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 16px;
  }
  
  button:hover {
    background-color: #45a049;
  }
  </style>
  