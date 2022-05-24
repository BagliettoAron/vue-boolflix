<template>
<div class="input-section">
    <input 
    type="text" 
    name="" 
    id=""
    placeholder="Search"
    v-model="searchedFilm"
    />

    <button @click='$emit("searchClicked", searchedFilm )' > Search </button>


</div>
  
</template>

<script>
export default {
    name: 'SearchBar',
    data: function () {
        return{
            searchedFilm: ''
        }
    }

}
</script>

<style>

</style>