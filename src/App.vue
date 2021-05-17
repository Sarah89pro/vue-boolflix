<template>
<div id="app">

  <!--Header-->
  <Header @getMovie="getMovie"/>

  <!--Main-->
  <Main :movies="movies" :tv="tvShow"/>
</div>
</template>

<script>

import axios from 'axios';
import Header from '@/components/Header.vue';
import Main from '@/components/Main.vue';

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },

  data() {
    return {
      apiURL: 'https://api.themoviedb.org/3/search/',
      apiKey: '17720c642e077ecf8786557e53897ffa',
      movies: [],
      tvShow: [],
    }
  },

  methods: {
    getMovie(search) {

      if(search !== '') {
        const apiParams = {
          api_key: this.apiKey,
          query: search,
          language: 'it-IT'
        };

        //FILM
        axios.get(this.apiURL + 'movie', {
          params: apiParams,
            
        }).then(res => {
          this.movies = res.data.results;
        });

        //TV
        axios.get(this.apiURL + 'tv', {
          params: apiParams,
        }).then(res => {
          this.tvShow = res.data.results;
        });
      }
    }
  }
}
</script>

<style lang="scss">
@import '@/styles/general';
</style>