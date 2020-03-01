<template>
  <ul>
    <li v-for="movie in movies" :key="movie.id">
        <Movie :movie="movie"/>
    </li>
  </ul>
</template>

<script>
import Movie from "./Movie";

export default {
  data() {
    return {
      movies: []
    };
  },

  created: function() {
    this.movieData();
  },

  methods: {
    movieData: async function() {
      try {
        const res = await fetch(
          "https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&api_key=0deb5d41f34c1edcac0a8f6f6d80f7e5"
        );
        const movies = await res.json();
        this.movies = movies.results;
      } catch (e) {
        console.log(e);
      }
    }
  },

  components: {
    Movie
  }
};
</script>

<style scoped>
ul {
  display: grid;
  list-style: none;
  padding: 1rem;
  margin: 0;
  grid-row-gap: 1rem;
  grid-template-columns: repeat(6, 1fr);
}
</style>