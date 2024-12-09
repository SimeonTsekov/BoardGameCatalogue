<template>
  <div class="filter-board-games">
    <label for="filter">Filter Games by Name:</label>
    <input
      type="text"
      id="filter"
      v-model="filterText"
      placeholder="Enter a game name"
    />
  </div>
</template>

<script setup>
import { defineModel } from "vue";

// Define a two-way bound model for `filterText`
defineModel({
  filterText: String,
});
</script>

<style scoped>
.filter-board-games {
  margin: 15px 0;
  text-align: left;
}

input {
  width: 100%;
  padding: 8px;
  margin-top: 5px;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
}
</style>