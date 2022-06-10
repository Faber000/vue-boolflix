<template>
    <header class="header">
        <form @submit.prevent="searching">
            <input type="text" v-model="searchText">
            <button>Search</button>
        </form>
        <div class="results">

            <h1>Film</h1>
            <div class="film" v-for="movie in shared.SharedFilms" :key="movie.id">
                <div>
                    Titolo: {{movie.title}}
                </div>
                <div>
                    Titolo originale: {{movie.original_title}}
                </div>
                <div>
                    <lang-flag :iso="(movie.original_language)"/>
                </div>
                <div>
                    Voto: {{movie.vote_average}}
                </div>
            </div>

            <h1>Serie Tv</h1>
            <div class="serie" v-for="serie in shared.SharedtvSeries" :key="serie.id">
                <div>
                    Titolo: {{serie.name}}
                </div>
                <div>
                    Titolo originale: {{serie.original_name}}
                </div>
                <div>
                    <lang-flag :iso="(serie.original_language)"/>
                </div>
                <div>
                    Voto: {{serie.vote_average}}
                </div>
            </div>
        </div> 
    </header>
</template>

<script>
import shared from '../../shared/data.js'
import axios from 'axios'

export default {
    name: 'BaseHeader',
    data() {
        return {
            searchText: '',
            shared,
        }
    },

    methods: {
        searching() {
            axios.get('https://api.themoviedb.org/3/search/movie',
                    {
                        params: {
                            api_key: 'ae54bc9c4c06af63c995413eb44a9dac',
                            query: this.searchText,
                            language: 'it-IT'
                        }
                    }
                ).then((response) => {
                    shared.SharedFilms = response.data.results;
                }).catch((error) => {
                    console.log(error);
                })

                axios.get('https://api.themoviedb.org/3/search/tv',
                    {
                        params: {
                            api_key: 'ae54bc9c4c06af63c995413eb44a9dac',
                            query: this.searchText,
                            language: 'it-IT'
                        }
                    }
                ).then((response) => {
                    shared.SharedtvSeries = response.data.results;
                }).catch((error) => {
                    console.log(error);
                })
        }
    }
}

</script>

<style lang="scss" scoped>
.header {
    margin: 20px;
}
.film, .serie {
    margin-bottom: 30px;
}

.film > *, .serie > * {
    margin-bottom: 10px;
}
</style>
