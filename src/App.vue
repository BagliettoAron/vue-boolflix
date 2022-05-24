<template>
  <div id="app">
    <SearchBar @searchClicked='sendAlbumRequest($event)'/>
    <MainContent />
  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue';
import MainContent from './components/MainContent.vue';

//import axios from 'axios'



export default {
  name: 'App',
  components: {
    SearchBar,
    MainContent
  },
  data () {
    return {
      films: []
    }
  },
  methods: {
    sendAlbumRequest: function (searchInput) {
      
    }


  }
}
</script>

<style lang="scss">
#app {

}
</style>
