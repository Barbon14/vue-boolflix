<template>
    <header>
        <input 
            type="text" 
            v-model="textSearch"
            @keyup.enter="getMovies"
        >
        <button @click.prevent="getMovies">
            Cerca
        </button>
    </header>
</template>

<script>
import axios from 'axios';

export default {
    name : 'App',

    data () {
        return {
            textSearch : "",
            // dati api
            apiUrl: "https://api.themoviedb.org/3/",
            apiKey: 'api_key=327423a3fa358699db3662c3a02c5b5e',
            apiMoviesSerch: 'search/movie?',

            movies: []

        }
    },
    methods: {
        getMovies() {
            axios
            .get(`${this.apiUrl}${this.apiMoviesSerch}${this.apiKey}&query=${this.textSearch}`)
            .then((result) => {
                this.movies = result.data.results;
                console.log(this.movies);
            })
            .catch((err) => {
                console.log(err);
            })
        }
    }
}
</script>

<style lang="scss" scoped>

</style>