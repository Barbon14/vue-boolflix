<template>
    <div class="card">
        <h3>
            {{ info.title }}
        </h3>
        <h4>
            {{ info.original_title }}
        </h4>
        <h5>
            {{ info.original_language }}
        </h5>
        <h5>
            {{ info.vote_average }}
        </h5>
    </div>
</template>

<script>
export default {
    name : 'Card',
    props: {
        info: Object
    }
}
</script>

<style lang="scss" scoped>
.card {
    margin: 30px;
}
</style>