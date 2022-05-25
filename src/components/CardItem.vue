<template>
  <div class="card-wrapper">
    <h2>{{ thisItem.title || thisItem.name }}</h2>
    <h4>
      Original title: {{ thisItem.original_title || thisItem.original_name }}
    </h4>
    <img
      v-if="imageFound"
      :src="require(`../assets/img/${thisItem.original_language}.png`)"
      alt="thisItem.original_language"
    />
    <div v-else class="">
      <img :src="require('../assets/img/not_found.png')" alt="Flag not found" />
      <p>Original Language: {{ thisItem.original_language }}</p>
    </div>
    <p>Rates: {{ thisItem.vote_average }}</p>
    <div>
      <i v-for="n in 5" :key="n" :class="n <= ratingsStars ? 'fas' : 'far'" class="fa-star"></i>
    </div>
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
      flagImages: ["en", "it"],
    };
  },
  computed: {
    imageFound() {
      return this.flagImages.includes(this.thisItem.original_language);
    },
    ratingsStars() {
      return Math.ceil(this.thisItem.vote_average / 2);
    }
  },
};
</script>

<style lang="scss" scoped>
@import '~@fortawesome/fontawesome-free/css/all.min.css';

.card-wrapper {
  img {
    height: 2rem;
  }

  width: calc(100% / 4 - 16px);
  margin: 8px;
  background-color: aliceblue;
  text-align: center;
  line-height: 2rem;
  padding: 2rem;
}
</style>
