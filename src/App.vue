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
  data(){
    return {
      movies: [],
      tvShow: [],
    }
  },
  methods:{
    getMovie(search){
      //FILM
      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: '17720c642e077ecf8786557e53897ffa',
          query: search,
        }
      })
      .then(res => {
        this.movies = res.data.results;
      })
      .catch(err => {
        console.log(err);
      });
      //TV
      axios.get('https://api.themoviedb.org/3/search/tv', {
        params: {
          api_key: '17720c642e077ecf8786557e53897ffa',
          query: search,
        }
      })
      .then(res => {
        this.tvShow = res.data.results;
      })
      .catch(err => {
        console.log(err);
      });
    }
  }
}
</script>

<style lang="scss">
@import '@/styles/general';
</style>