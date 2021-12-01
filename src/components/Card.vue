<template>
    <div class="card">
        {{ info.title }}
        {{ info.original_title }}
        {{ info.original_language }}
        {{ info.vote_average }}
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

</style>