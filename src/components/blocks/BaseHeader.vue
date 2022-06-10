<template>
    <header>
        <form @submit.prevent="searching">
            <input type="text" v-model="searchText">
            <button>Search</button>
        </form>
        <div v-for="movie in shared.SharedFilms" :key="movie.id">{{movie.title}}</div>
    </header>
</template>

<script>
import shared from '../../shared/data.js'
import axios from 'axios';

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
        }
    }
}
</script>

<style lang="scss" scoped>

</style>
