<template>
<transition name="fade">
    <div class="movie-wrapper" :style="styles">
        <div class="movie-info">
            <h1>{{ movie.title }}</h1>
            <h3>Release date: {{ movie.release_date }}</h3>
            <p>{{ movie.overview }}</p>
        </div>
    </div>
</transition>
</template>

<script>
const backgroundImage = "http://image.tmdb.org/t/p/w1280";

export default {
  data() {
    return {
      movie: {}
    };
  },

  created: function() {
    this.movieDetail();
  },

  methods: {
    movieDetail: async function() {
      const res = await fetch(
        `https://api.themoviedb.org/3/movie/${this.$route.params.id}?api_key=0deb5d41f34c1edcac0a8f6f6d80f7e5`
      );
      const movie = await res.json();
      this.movie = movie;
    }
  },

  computed: {
    styles() {
      return {
        background: `url(${backgroundImage}/${this.movie.backdrop_path}) no-repeat center`
      };
    }
  }
};
</script>

<style scoped>
.movie-wrapper {
  position: absolute;
  position: relative;
  padding-top: 50vh;
  background-size: cover;
}

.movie-info {
  background: #fff;
  color: #222;
  padding: 2rem 10rem;
}

.fade-enter-active,
.fade-leave-active {
  transition: all 0.4s ease-in-out;
  transform: translateX(-100%);
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
  transform: translateX(100%);
}
</style>