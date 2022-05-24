<template>
  <div id="app">
    <SearchBar 
    @searchClicked='getAll($event)'
    />
    <MainContent :movies='films' :series='serieTV'
/>
  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue';
import MainContent from './components/MainContent.vue';
import axios from 'axios';



export default {
  name: 'App',
  components: {
    SearchBar,
    MainContent
  },
  data () {
    return {
      serieTV: [],
      films: [],
      apiKey: 'bf841d7ca9d819f77ccf85011ba3d739'
    }
  },
  methods: {
    getAll(searchInput) {
      this.sendAlbumRequest(searchInput),
      this.sendSerieTVRequest(searchInput)
    },
    
    sendAlbumRequest: function (searchInput) {
      axios
      .get ('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: this.apiKey,
          query: searchInput
        }
      })
      .then (resp => {
        this.films = resp.data.results;
        console.log(this.films);
      })
    },
  
    sendSerieTVRequest: function (searchInput) {
      axios
      .get ('https://api.themoviedb.org/3/search/tv', {
        params: {
          api_key: this.apiKey,
          query: searchInput
        }
      })
      .then (resp => {
        this.serieTV = resp.data.results;
        console.log(this.serieTV);
      })
    }
  },

}
</script>

<style lang="scss">
@import './style/common.scss'

</style>
