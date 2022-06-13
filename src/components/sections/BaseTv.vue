<template>
    <section>
        <div v-if="shared.SharedtvSeries.length > 0" class="serie-container container">
            <h1>Serie Tv</h1>
            <div class="row d-flex justify-content-center">
                <div class="serie col-lg-2 my-3" v-for="serie in shared.SharedtvSeries" :key="serie.id">
                    <img class="serie-img" :src="makeUrl(serie.poster_path)" alt="">
                    <div class="text-container">
                        <div>Titolo: {{serie.name}}</div>
                        <div>Titolo originale: {{serie.original_name}}</div>
                        <div>
                            <lang-flag :iso="(serie.original_language)"/>
                        </div>
                        <div class="stars-container">
                            <div :key="index" v-for="(star,index) in stars(serie.vote_average)"><font-awesome-icon class="icon" icon="fa-solid fa-star"/></div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>

import shared from '../../shared/data.js'

export default {
    name: 'BaseTv',
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
                return `https://via.placeholder.com/185x280?text=No Image`
            } else 

            {
                return `https://image.tmdb.org/t/p/w185/${url}`
            }
        },

        stars(vote) {
            return Math.floor(vote/2);
        }
    }
}

</script>

<style lang="scss" scoped>

.serie-container {
     text-align: center;
}

.serie {
    position: relative;   
    margin-right: 20px;
} 

.serie-img {
    display: block;
}

.serie:hover .text-container{
  background-color: #000;
  width: 200px;
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