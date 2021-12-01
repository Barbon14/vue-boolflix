<template>
  <div id="app">
    <AppHeader @moviesListReady="setMoviesList"/>
    <AppMain :moviesList="moviesList"/>
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
      moviesList: []
    }
  },
  methods: {
    setMoviesList(array) {
      this.moviesList = array;
    }
  }
}
</script>

<style lang="scss">
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
</style>
