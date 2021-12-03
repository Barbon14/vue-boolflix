<template>
    <main>
        <section class="movies">
            <h2>
                Film
            </h2>
            <div class="container">
                <Card 
                    v-for="movie in moviesList" 
                    :key="movie.id"
                    :info="movie"
                />
            </div>
        </section>
        <section class="tv-series">
            <h2>
                Serie TV
            </h2>
            <div class="container">
                <Card 
                    v-for="show in tvSeriesList" 
                    :key="show.id"
                    :info="show"
                />
            </div>
        </section>
    </main>
</template>

<script>
import Card from '@/components/Card.vue'

export default {
    name : 'AppMain',
    components: {
        Card
    },
    props: {
        moviesList: Array,
        tvSeriesList: Array
    }
}
</script>

<style lang="scss" scoped>
main {
    height: calc(100vh - 80px);
    background-color: #1b1b1b;
    overflow-y: auto;
    color: white;

    section {
        padding: 20px;
    }
    .container {
        padding: 20px 0;
        display: flex;
        overflow-x: auto;
    }
}
</style>