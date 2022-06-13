<template>
    <section>
        <h1>Film</h1>
        <div class="film-container">
            <div class="film" v-for="movie in shared.SharedFilms" :key="movie.id">
                <img class="film-img" :src="makeUrl(movie.poster_path)" alt="">
                <div class="text-container">
                    <div>Titolo: {{movie.title}}</div>
                    <div>Titolo originale: {{movie.original_title}}</div>
                    <div class="stars-container">
                        <div :key="index" v-for="(star,index) in stars(movie.vote_average)"><font-awesome-icon class="icon" icon="fa-solid fa-star"/></div>
                    </div>
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
            if(url == null) {
                return `https://via.placeholder.com/185x280?text=No image`
            } else 

            {
                return `https://image.tmdb.org/t/p/w185/${url}`
            }
            
        },

        stars(vote) {
            return Math.floor(vote/2);
        }
    },
}

</script>

<style lang="scss" scoped>

section {
    margin: 20px;
}

.film-container {
    display: flex;
    position: relative;
}

.film {
    position: relative;
    margin-right: 20px;
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
}

.text-container > div {
    margin-bottom: 5px;
}

.text-container {
    display: none;
    color: white;
}

.stars-container {
    display: flex;
}

.icon {
    color: yellow;
}
</style>
