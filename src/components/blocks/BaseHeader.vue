<template>
    <header class="header">
        <nav>
            <img class="logo" src="../../assets/img/logo.png" alt="">

            <form @submit.prevent="searching">
                <input type="text" v-model="searchText">
                <button class="btn btn-danger mx-2" >Search</button>
            </form>
        </nav>
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


nav {
    height: 80px;
    width: 100%;
    background-color: black;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.logo {
    height: 100%;
}

 
</style>