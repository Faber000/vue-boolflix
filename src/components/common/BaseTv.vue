<template>
    <section>
        <h1>Serie Tv</h1>
        <div class="serie-container">
            <div class="serie" v-for="(serie,index) in shared.SharedtvSeries" :key="serie.id">
                <img class="serie-img" v-if="index<7" :src="makeUrl(serie.poster_path)" alt="">
                <div class="text-container">
                    <div>Titolo: {{serie.name}}</div>
                    <div>Titolo originale: {{serie.original_name}}</div>
                    <div>Voto: {{serie.vote_average}}</div>
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
            return `https://image.tmdb.org/t/p/w185/${url}`
        }
    }
}

</script>

<style lang="scss" scoped>

section {
    margin: 20px;
}

.serie-container {
    display: flex;
    margin-bottom: 30px;
}

.serie {
    margin-right: 20px; 
    position: relative;   
} 

.serie-img {
    display: block;
}

.serie:hover .text-container{
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