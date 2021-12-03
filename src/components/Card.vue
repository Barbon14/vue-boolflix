<template>
    <div class="card">
        <img class="poster"
            :src="info.poster_path != null ? `https://image.tmdb.org/t/p/w342${info.poster_path}` : 'https://i.pinimg.com/236x/a4/3b/29/a43b2945c7a69102ef193ad7418c32a0.jpg'" 
            :alt="info.title ? info.title : info.name"
        >
        <div class="card_info">
            <h3>
                {{ info.title }}
                {{ info.name }}
            </h3>
            <h4>
                {{ info.original_title }}
                {{ info.original_name }}
            </h4>
            <img
                class="language_flag"
                v-if="languagesImgs.includes(info.original_language)"
                :src="require(`../assets/img/${info.original_language}.png`)" 
                :alt="info.original_language"
            >
            <div v-else>
                {{ info.original_language }}
            </div>
            <div>
                <span v-for="n in voteRounded" :key="n">
                    <i class="fas fa-star"></i>
                </span>
            </div>
        </div>
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
            voteRounded: Math.ceil(this.info.vote_average / 2)
        }
    }
}
</script>

<style lang="scss" scoped>
.card {
    margin: 10px;
    color: white;
    position: relative;
    width: calc((100vw / 5) - 20px);
    // height: 500px;
    flex-shrink: 0;

    .poster { 
        width: 100%;
        height: 100%
    };

    .card_info {
        position: absolute;
        top: 0;
        left: 0;
        padding: 20px;
        display: none;

        .language_flag {
            width: 50px;
            height: 30px;
        }
    }

    &:hover  {
        .card_info{
            display: block;
        }
        .poster {
            opacity: 0.4;
        }
    }
}
</style>