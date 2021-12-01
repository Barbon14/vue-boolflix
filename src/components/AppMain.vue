<template>
    <main>
        <Card 
            v-for="movie in moviesList" 
            :key="movie.id"
            :info="movie"
        />
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
        moviesList: Array
    }
}
</script>

<style lang="scss" scoped>

</style>