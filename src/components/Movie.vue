<template>
    <section class="movie">
        
        <!--title-->
        <h4>
            <strong>Titolo:</strong>
            {{ movie.title !== undefined ? movie.title : movie.name }}</h4>
            
        <h4>
            <strong>Titolo originale:</strong>
            {{ movie.original_title !== undefined ? movie.original_title : movie.original_name }}</h4>
        

        <!--img-->
        <img :src="`https://image.tmdb.org/t/p/w185${movie.poster_path}`" alt="movie poster">

        <ul>

            <!--langs-->
            <li>
                <strong>Lingua:</strong>
                <img
                v-if="movie.original_language === 'en'"
                src="../assets/img/en.png" alt="lang en">

                <img
                v-else-if="movie.original_language === 'it'"
                src="../assets/img/it.png" alt="lang it">

                <span
                v-else>{{ movie.original_language }}</span>
            </li>
            
            <!--vote-->
            <li>
                <strong>Voto: </strong>
                <span
                v-for="(vote, index) in Math.ceil(movie.vote_average / 2)"
                :key="index">
                <i class="fas fa-star"></i></span>

                <span
                v-for="(vote, index) in 5 - Math.ceil(movie.vote_average / 2)"
                :key="index"><i class="far fa-star"></i></span>
            </li>
            
        </ul>
    </section>
</template>

<script>
export default {
    name: 'Movie',
    props: ['movie'],
}
</script>

<style scoped lang="scss">
@import '../styles/vars';


.movie {
    width: 300px;
    margin-right: 50px;
    margin-bottom: 50px;
}


img {
        width: 30px;
        margin-left: 5px;
}

</style>