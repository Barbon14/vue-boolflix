<template>
  <div id="app">
    <AppHeader 
      @moviesListReady="setMoviesList"
      @tvSeriesListReady="setTvSeriesList"
    />
    <AppMain 
      :moviesList="moviesList" 
      :tvSeriesList="tvSeriesList"
    />
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';

export default {
  name: 'App',
  components: {
    AppHeader,
    AppMain
  },
  data() {
    return {
      moviesList: [],
      tvSeriesList: []
    }
  },
  methods: {
    setMoviesList(array) {
      this.moviesList = array;
    },
    setTvSeriesList(array) {
      this.tvSeriesList = array;
    }
  }
}
</script>

<style lang="scss">
@import '~@fortawesome/fontawesome-free/css/all.min.css';

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: sans-serif;
}
</style>