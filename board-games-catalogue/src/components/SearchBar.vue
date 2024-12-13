<template>
  <div class="topnav">
    <button @click="addGame">
      <i class="fa fa-plus"></i>
    </button>
    <div class="search-bar">
      <button  >
        <i class="fa fa-search"></i>
      </button>
      <input
        type="text"
        v-model="searchQuery"
        placeholder="Search games..."
        @input="updateQuery"
      />
    </div>
  </div>
</template>

<script>
import { defineComponent, ref } from "vue";
import "@/assets/navigation-bar.css"

export default defineComponent({
  name: "SearchBar",
  emits: [
    "update-query",
    "add-game"
  ],
  setup(_, { emit }) {
    const searchQuery = ref("");

    const updateQuery = () => {
      emit("update-query", searchQuery);
    };

    const addGame = () => {
      emit("add-game");
    };

    return {
      searchQuery,
      updateQuery,
      addGame
    };
  },
})
</script>
