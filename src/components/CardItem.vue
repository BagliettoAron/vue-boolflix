<template>
  <div class="card-wrapper">

  <div class="card-info">
    <h2>{{ thisItem.title || thisItem.name }}</h2>
    <h4>
      Original title: {{ thisItem.original_title || thisItem.original_name }}
    </h4>
    <div class="language-flag" v-if="imageFound">
      <img
        :src="require(`../assets/img/${thisItem.original_language}.png`)"
        alt="thisItem.original_language"
      />
    </div>
    <div v-else class="flag-not-found">
      <img :src="require('../assets/img/not_found.png')" alt="Flag-not-found" />
      <p>Original Language: {{ thisItem.original_language }}</p>
    </div>
    <div>
      <i
        v-for="n in 5"
        :key="n"
        :class="n <= ratingsStars ? 'fas' : 'far'"
        class="fa-star"
      ></i>
    </div>

  </div>

  <div class="card-poster">
  
    <div class="poster" v-if="thisItem.poster_path != null">
      <img
        :src="`https://image.tmdb.org/t/p/w92/${thisItem.poster_path}`"
        alt="Album image"
      />
    </div>

    <div class="poster-not-found" v-else>
      <img
        :src="require('../assets/img/not_found.png')"
        alt="Poster-not-found"
      />
    </div>
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
    },
  },
};
</script>

<style lang="scss" scoped>
@import "~@fortawesome/fontawesome-free/css/all.min.css";

.flag-not-found img,
.language-flag img {
  height: 2rem;
}

.poster-not-found img {
  height: 6rem;
}

.card-wrapper {
  width: calc(100% / 4 - 16px);
  margin: 8px;
  background-color: aliceblue;
  text-align: center;
  line-height: 2rem;
  padding: 2rem;
  height: 25rem;


}
.card-poster{
  display: none;
}

.card-wrapper:hover{

  .card-poster{
  display: block;
  transition-duration: 3000ms;
  }

  .card-info{
    display: none;
    transition-duration: 3s;
  } 
}


</style>
