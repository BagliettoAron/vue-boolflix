<template>
  <div class="card-wrapper">
    <h2>{{ thisItem.title || thisItem.name }}</h2>
    <h4>
      Original title: {{ thisItem.original_title || thisItem.original_name }}
    </h4>
    <img v-if='imageFound()' :src="require(`../assets/img/${thisItem.original_language}.png`)" alt="thisItem.original_language">
    <div v-else class="">
      <img :src="require('../assets/img/not_found.png')" alt="Flag not found">
      <p>Original Language: {{ thisItem.original_language}}</p>
    </div>
    <small>Rates: {{ thisItem.vote_average }}</small>
  </div>
</template>

<script>
export default {
  name: "CardItem",
  props: {
    thisItem: Object,
  },
  data() {
    return {
      flagImages : ['en', 'it']
    }
  },
  methods: {
    imageFound () {
      return this.flagImages.includes(this.thisItem.original_language);

    }
  }
};
</script>

<style lang="scss" scoped>
.card-wrapper {

  img{
    width: 3rem;
  }
  width: calc(100% / 4 - 16px);
  margin: 8px;
  background-color: aliceblue;
  text-align: center;
  line-height: 2rem;
  padding: 2rem;
}
</style>
