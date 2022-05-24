<template>
  <div class="card-wrapper">
    
      <h2>{{thisItem.title || thisItem.name}}</h2>
      <h4>Original title: {{ thisItem.original_title || thisItem.original_name }}</h4>
      <p>Original Language: {{thisItem.original_language}}</p>
      <small>Rates: {{thisItem.vote_average}}</small>
    
  </div>
</template>

<script>
export default {
  name: "CardItem",
  props: {
    thisItem: Object,
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
