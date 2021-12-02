<template>
    <div class="card">
        <img 
            :src="`https://image.tmdb.org/t/p/w342${info.poster_path}`" 
            :alt="info.title ? info.title : info.name"
        >
        <h3>
            {{ info.title }}
            {{ info.name }}
        </h3>
        <h4>
            {{ info.original_title }}
            {{ info.original_name }}
        </h4>
        <img
            v-if="languagesImgs.includes(info.original_language)"
            :src="require(`../assets/img/${info.original_language}.png`)" 
            :alt="info.original_language"
        >
        <div v-else>
            {{ info.original_language }}
        </div>
        <h5>
            <span v-for="n in Math.ceil(info.vote_average / 2)" :key="n">
                
                <i class="fas fa-star"></i>
            </span>
        </h5>
    </div>
</template>

<script>
export default {
    name : 'Card',
    props: {
        info: Object
    },
    data() {
        return {
            languagesImgs: ['it', 'en'],
        }
    }
}
</script>

<style lang="scss" scoped>
.card {
    margin: 30px;
}
</style>