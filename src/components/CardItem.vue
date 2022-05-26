<template>
  <div class="card-wrapper">
    <div class="card-info">
      <h2 class="bold" >{{ thisItem.title || thisItem.name }}</h2>
      <h4>
        <span class="bold">Original title :</span> {{ thisItem.original_title || thisItem.original_name }}
      </h4>
      <div class="language-flag" v-if="imageFound">
        <img
          :src="require(`../assets/img/${thisItem.original_language}.png`)"
          alt="thisItem.original_language"
        />
      </div>
      <div v-else class="flag-not-found">
        <img
          :src="require('../assets/img/not_found.png')"
          alt="Flag-not-found"
        />
        <p>  <span class="bold">Original Language :</span> {{ thisItem.original_language }}</p>
      </div>
      <div class="ratings" >
      <span class="bold"> Ratings :</span>
        <i
          v-for="n in 5"
          :key="n"
          :class="n <= ratingsStars ? 'fas' : 'far'"
          class="fa-star"
        ></i>
      </div>
      <div class="overview">
        <p v-if="thisItem.overview"> <span class="bold">Overview :</span> {{thisItem.overview}} </p>
        <p v-else><span class="bold">Overview :</span> not-found</p>
      </div>
    </div>

    <div class="card-poster">
      <div class="poster" v-if="thisItem.poster_path != null">
        <img
          :src="`https://image.tmdb.org/t/p/w342/${thisItem.poster_path}`"
          alt="Album image"
        />
      </div>

      <div class="poster-not-found" v-else>
        <div class="poster-not-found__image">
          <img
            :src="require('../assets/img/not_found.png')"
            alt="Poster-not-found"
          />
        </div>
        <div class="poster-not-found__title">
          <h2>{{ thisItem.title || thisItem.name }}</h2>
        </div>
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
@import '../style/variables.scss';

.card-info {
  width: 100%;
  height: 100%;
}

.flag-not-found img,
.language-flag img {
  height: 2rem;
}

.poster img {
  width: 100%;
  height: 100%;
}

.card-wrapper {
  width: 342px;
  height: 517px;
  margin: 8px;
  text-align: center;
}

.card-info {
  display: none;
}

.card-wrapper:hover {
  .card-info {
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;
    background-color: $background-card-color;
    color:$text-color-card;
    transition: background-color 2s;
  }

  .card-poster {
    display: none;
    transition: background-color 2s;
    
  }
}

.poster-not-found {
  align-items: center;

  &__title{
    margin-top: 3rem;
  }
}

.bold{
  color: $classBold-text-color;
  font-weight: 700;
}

.ratings{
  color: $ratings-stars-color;
}
</style>
