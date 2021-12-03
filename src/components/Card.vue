<template>
    <div class="card">
        <!-- poster -->
        <img class="poster"
            :src="info.poster_path != null ? `https://image.tmdb.org/t/p/w342${info.poster_path}` : 'https://i.pinimg.com/236x/a4/3b/29/a43b2945c7a69102ef193ad7418c32a0.jpg'" 
            :alt="info.title ? info.title : info.name"
        >
        <div class="card_info">
            <!-- title -->
            <h3>
                {{ info.title }}
                {{ info.name }}
            </h3>
            <!-- original title -->
            <h4>
                Titolo orginale:
            </h4>
            <div>
                {{ info.original_title }}
                {{ info.original_name }}
            </div>
            <!-- original language -->
            <div class="orig_language">
                <h4>
                    Lingua originale:
                </h4> 
                <img
                    v-if="languagesImgs.includes(info.original_language)"
                    :src="require(`../assets/img/${info.original_language}.png`)" 
                    :alt="info.original_language"
                >
                <div v-else>
                    {{ info.original_language }}
                </div>
            </div>
            <!-- vote icons -->
            <h4>
                Voto medio:
            </h4> 
            <div v-if="voteRounded != 0">
                <span v-for="n in voteRounded" :key="n">
                    <i class="fas fa-star"></i>
                </span>
            </div>
            <div v-else>
                Ancora nessun voto 
            </div>
            <!-- overview -->
            <p class="overview" v-if="info.overview != ''">
                <strong>Trama: </strong> {{ info.overview }}
            </p>
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
    width: 300px;
    height: 450px;
    flex-shrink: 0;

    .poster { 
        width: 100%;
        height: 100%
    };

    .card_info {
        width: 100%;
        height: 100%;
        padding: 20px;
        text-align: center;
        // position
        position: absolute;
        top: 0;
        left: 0;
        // display
        display: none;
        flex-direction: column;
        align-items: center;
        justify-content: center;

        h3 {
            margin: 15px 0;
        }

        .orig_language {
            margin: 10px ;

            img {
                width: 50px;
                height: 30px;
                margin: 5px 0;
            }
        }

        span { 
            color: yellow;
        }

        .overview {
            margin: 10px 0;
            overflow: hidden;
            display: -webkit-box;
            -webkit-box-orient: vertical;
            -webkit-line-clamp: 5;
        }
    }

    &:hover  {
        .card_info{
            display: flex;
        }
        .poster {
            opacity: 0.4;
        }
    }
}
</style>