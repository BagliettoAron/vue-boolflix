<template>
  <div class="input-section">
    <input
      type="text"
      name=""
      id=""
      placeholder="Search"
      v-model="searchedFilm"
    />

    <button @click="$emit('searchClicked', searchedFilm)">Search</button>
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  data: function () {
    return {
      searchedFilm: "",
    };
  },
};
</script>

<style lang="scss" scoped>
.input-section {
  height: 5rem;
  background-color: aquamarine;
  display: flex;
  justify-content: center;
  align-items: center;

  input {
    margin: 0 2rem;
  }
}
</style>
