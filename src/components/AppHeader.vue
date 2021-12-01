<template>
    <header>
        <input 
            type="text" 
            v-model="textSearch"
            @keyup.enter="getData"
        >
        <button @click.prevent="getData">
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
            apiMoviesSearch: 'search/movie?',
            apiTvSeriesSearch: 'search/tv?',

            movies: [],
            tvSeries : []

        }
    },
    methods: {
        getData() {
            axios
            .get(`${this.apiUrl}${this.apiMoviesSearch}${this.apiKey}&query=${this.textSearch}`)
            .then((resMovie) => {
                this.movies = resMovie.data.results;
                this.$emit('moviesListReady', this.movies);
            })
            .catch((err) => {
                console.log(err);
            })
            axios
            .get(`${this.apiUrl}${this.apiTvSeriesSearch}${this.apiKey}&query=${this.textSearch}`)
            .then((resTv) => {
                this.tvSeries = resTv.data.results;
                this.$emit('tvSeriesListReady', this.tvSeries);
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