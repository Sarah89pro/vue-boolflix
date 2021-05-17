<template>
  <main>
    <!--FILM-->
    <section v-show="movies.length" class="movies">
      <h2>Film</h2>
      <ul>
        <li
        v-for="movie in movies" 
        :key="movie.id">
          <Movie
          :type="movie"
          />
        </li>
      </ul>
    </section>

    <!--TV-->
    <section v-show="tv.length" class="movies">
      <h2>Tv Show</h2>
      <ul>
        <li
        v-for="serie in tv" 
        :key="serie.id">
          <Movie 
          :type="serie"
          />
        </li>
      </ul>
    </section>

  </main>
</template>

<script>

import Movie from '@/components/Movie.vue';

export default {
  name: 'Main',
  components: {
    Movie
  },
  props: {
    movies: Array, tv: Array,
  }
}
</script>

<style scoped lang="scss">
@import '../styles/vars';

main {
  display: flex;
  flex-wrap: wrap;
}


ul {
  margin-top: 80px;
}

</style>