<template>
    <main>
        <section class="movies">
            <h2>
                Film
            </h2>
            <Card 
                v-for="movie in moviesList" 
                :key="movie.id"
                :info="movie"
            />
        </section>
        <section class="tv-series">
            <h2>
                Serie TV
            </h2>
            <Card 
                v-for="show in tvSeriesList" 
                :key="show.id"
                :info="show"
            />
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

</style>