<template>
  <div class="add-board-game">
    <h2>Add a New Board Game</h2>
    <form @submit.prevent="submitForm">
      <div class="form-group">
        <label for="name">Name:</label>
        <input
          type="text"
          id="name"
          v-model="boardGame.name"
          placeholder="Enter board game name"
          required
        />
      </div>

      <div class="form-group">
        <label for="image">Image URL:</label>
        <input
          type="url"
          id="image"
          v-model="boardGame.image"
          placeholder="Enter image URL"
          required
        />
      </div>

      <div class="form-group">
        <label for="description">Description:</label>
        <textarea
          id="description"
          v-model="boardGame.description"
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
export default {
  data() {
    return {
      boardGame: {
        name: "",
        image: "",
        description: "",
      },
    };
  },
  methods: {
    submitForm() {
      this.$emit("add-game", { ...this.boardGame });
      this.resetForm();
    },
    resetForm() {
      this.boardGame = {
        name: "",
        image: "",
        description: "",
      };
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
  