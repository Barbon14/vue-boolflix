<template>
    <header>
        <input type="text" v-model="textSerch">
        <button @click.prevent="">Cerca</button>
    </header>
</template>

<script>
export default {
    name : 'App',

    data () {
        return {
            textSerch : "",
        }
    }
}
</script>

<style lang="scss" scoped>

</style>