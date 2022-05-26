<template>
<div class="header">

<div class="header__logo">
<img :src="require('../assets/img/netflix_logo.png')" alt="">
<small>Powered by Boolean &reg;</small>
</div>

<div class="input-section">
    <input
      type="text"
      name=""
      id=""
      placeholder="Insert Title"
      v-model="searchedFilm"
    />
    <button @click="$emit('searchClicked', searchedFilm)">Search</button>
</div>

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
@import '../style/variables.scss';

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: $header-bg-color;
  height: 100px;

  

  &__logo{

    small {
      font-style: italic;
      color: $netflix-color;
      font-size: .8rem;
      margin-left: .5rem;
      font-weight: 550;
    }

  img{
    width: 10rem;
    margin-left: 2rem;  
    background-color: black;
    }
  } 


}

.input-section {
  

  input {
    margin: 0 2rem;
    padding: .5rem 1rem;
    border-radius: 5px;
    border: 2px solid $netflix-color;


  }

    button {
      margin-right: 2rem;
      padding: .5rem 1rem;
      border-radius: 5px;
      border: 2px solid $netflix-color;
      background-color: $netflix-color;
      font-weight: 750;
      color: white;
    }

}
</style>
