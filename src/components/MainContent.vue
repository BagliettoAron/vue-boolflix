<template>
  <div class="wrap">
    <h2>Films</h2>
    <div class="main-section">
      <CardItem v-for="item in movies" :key="item.id" :thisItem="item" />
    </div>

    <h2>Serie TV</h2>
    <div class="main-section">
      <CardItem v-for="item in series" :key="item.id" :thisItem="item" />
    </div>
  </div>
</template>

<script>
import CardItem from "./CardItem.vue";

export default {
  name: "MainContent",
  components: {
    CardItem,
  },
  props: {
    movies: Array,
    series: Array,
  },
};
</script>

<style lang="scss" scoped>
.wrap {
  h2 {
    text-align: center;
    margin: 2rem 0;
  }
}

.main-section {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
