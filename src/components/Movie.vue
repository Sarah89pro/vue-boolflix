<template>

<section class="box">
    <div class="poster">
        <!--Poster-->
        <img v-if="type.poster_path" :src="`https://image.tmdb.org/t/p/w342${type.poster_path}`" alt="movie poster">
        <img class="unavailable" v-else src="@/assets/img/noposter.png" alt="poster unavailable">
    </div>

    <!--Details-->
    <div>
        <!-- title and langs-->
        <ul>
            <li>
                <strong>Titolo:</strong>
                {{ type.title !== undefined ? type.title : type.name }}
            </li>
            
            <li>
                <strong>Titolo originale:</strong>
                {{ type.original_title !== undefined ? type.original_title : type.original_name }}
            </li>

            <li>
                <strong>Lingua:</strong>
                   <img
                   v-if="isFlag(type.original_language)" 
                    :src="require(`@/assets/img/${type.original_language}.png`)" 
                    :alt="type.original_language"
                    class="flag">
                    <span v-else>{{ type.original_language }}</span>
            </li>

            <!--vote-->
            <li>
                <strong>Voto:</strong>
                <span
                v-for="i in getStarVote(type.vote_average)" 
                :key="`full-${i}`">
                    <i class="fas fa-star full"></i></span>

                <span
                v-for="i in 5 - getStarVote(type.vote_average)" 
                :key="`empty-${i}`">
                    <i class="far fa-star"></i></span>                
            </li>

            <!--overview-->
            <li class="overview">
                <strong>Overview:</strong>{{type.overview}}
            </li>
        </ul>
    </div>
    </section>

</template>

<script>

export default {
    name: 'Movie',
    props: {
        type: Object,
    },

    data() {
        return {
            flagsImg: ['it', 'en']
        }
    },

    methods: {
        isFlag(lang) {
            return this.flagsImg.includes(lang);
        },
        getStarVote(vote) {
            return Math.ceil(vote / 2);
        }
    }
}
</script>

<style scoped lang="scss">

@import '../styles/vars';

img {
    object-fit: cover;
}

.box {
    height: 500px;
    width: 350px;
    margin: 0 5px 0 20px;
    overflow: hidden;
    cursor: pointer;
    position: relative;  
}


.poster {
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;
    width: 100%;
}


ul {
    position: absolute;
    top: 50%;
    left: 16px;
    transform: translateY(-50%);
    color: $white;
    opacity: 0;
    transition: opacity 0.3s;
    z-index: 1;
}


li {
    margin-bottom: 16px;
}


li i {
    margin-left: 5px;
}


.full {
    color: $yellow;
}


.flag {
    width: 25px;
    margin-left: 5px;
        
}

.overview {
    height: 180px;
    margin-bottom: 10px;
    overflow: hidden;
    text-overflow: ellipsis;
}


.box::after {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;
    width: 100%;
    background-color: $black-a;
    opacity: 0;
    transition: opacity 0.3s;
}


.box:hover::after,
.box:hover ul {
    opacity: 1;
}

</style>