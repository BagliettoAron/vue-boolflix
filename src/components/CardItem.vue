<template>
  <div class="card-wrapper">
    
      <h2 class="title" >{{thisMovie.title}}</h2>
      <h4 class="original-title" >Original title: {{ thisMovie.original_title }}</h4>
      <p class="language" >Original Language: {{thisMovie.original_language}}</p>
      <small class="rates" >Rates: {{thisMovie.vote_average}}</small>
    
  </div>
</template>

<script>
export default {
  name: "CardItem",
  props: {
      thisMovie: Object,
      thisSerie: Object
  }
};
</script>

<style lang="scss" scoped>


.card-wrapper {
    width: calc(100% / 4 - 16px);
    margin: 8px;
    background-color: aliceblue;
    text-align: center;
    line-height: 2rem;
    padding: 2rem;
}

</style>
