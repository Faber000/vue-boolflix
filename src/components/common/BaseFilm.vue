<template>
    <section>
        <h1>Film</h1>
        <div class="film-container">
            <div class="film" v-for="(movie, index) in shared.SharedFilms" :key="movie.id">
                <img class="film-img" v-if="index<7" :src="makeUrl(movie.poster_path)" alt="">
                <div class="text-container">
                    <div>Titolo: {{movie.title}}</div>
                    <div>Titolo originale: {{movie.original_title}}</div>
                    <div>Voto: {{movie.vote_average}}</div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>

import shared from '../../shared/data.js'

export default {
    name: 'BaseFilm',
    components: {
        
    },

    data() {
        return {
            shared,
        }
    },

    methods: {
        makeUrl(url) {
            return `https://image.tmdb.org/t/p/w185/${url}`
        }
    }
}

</script>

<style lang="scss" scoped>

section {
    margin: 20px;
}

.film-container {
    margin-bottom: 30px;
    display: flex;
    position: relative;
}

.film {
    margin-right: 20px;
    position: relative;
}

.film-img {
    display: block;
}

.film:hover .text-container{
  background-color: #000;
  width: 100%;
  height: 100%;
  display: block;
  position: absolute;
  content: "";
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  margin: auto;
  opacity: 0.7;
  padding: 5px;
}

.text-container > div {
    margin-bottom: 5px;
}

.text-container {
    display: none;
    color: white;
}
</style>
