<template>
    <main>
        <!--FILM-->
        <section class="movies">
            <h2>Film</h2>
            <ul>
                <li
                v-for= "entry in movies"
                :key="entry.id">
                <Movie
                :movie="entry"/>
                </li>
            </ul>
        </section>

        <!--TV-->
        <section class="movies">
            <h2>Tv Show</h2>
            <ul>
                <li
                v-for="entry in tv"
                :key="entry.id">
                <Movie
                :movie="entry"/>
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
        Movie,
    },
    props: {
        movies: Array, tv: Array,
    },
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