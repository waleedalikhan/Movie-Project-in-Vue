<template>
    <router-link :to="moviePath">
        <img :src="posterImage" :alt="posterAlt">
    </router-link>
</template>

<script>
const POSTER_PATH = "http://image.tmdb.org/t/p/w154"

export default {
    props: ['movie'],

    computed: {
        posterImage: function() {
            return `${POSTER_PATH}/${this.movie.poster_path}`
        },
        posterAlt: function() {
            return this.movie.title
        },
        moviePath: function() {
            return `/movie/${this.movie.id}`
        }
    }

}
</script>

<style scoped>
img {
    box-shadow: 0 0 35px #222;
}
</style>