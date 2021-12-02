<template>
    <header>
        <img src="https://upload.wikimedia.org/wikipedia/commons/0/08/Netflix_2015_logo.svg" alt="">
        <span>
            <input 
                type="text" 
                v-model="textSearch"
                @keyup.enter="getData"
            >
            <button @click.prevent="getData">
                Cerca
            </button>
        </span>
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
header {
    height: 80px;
    background-color: black;
    padding: 20px;
    display: flex;
    align-items: center;
    justify-content: space-between;

    img {
        height: 100%;
    }

    input {
        margin: 0 10px;
        padding: 3px;
    }

    button {
        padding: 3px;
    }
}
</style>