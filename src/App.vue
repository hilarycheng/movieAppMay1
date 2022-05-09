<template>
  <nav>
    <a href="">Films</a>
    <a href="">TV programmes</a>
    <a href="">Watch</a>
    <a href="">Sign in </a>
  </nav>

  <movie-detail />

  <h2>Popular movies</h2>

  <div>
    <li v-for="movie of movies" :key="movie.id"> {{movie.title}}
      <a href="www.google.com"><img v-bind:src="'https://image.tmdb.org/t/p/w500' + movie.poster_path "  alt="img"></a>
    </li>
  </div>


</template>

<script>
import axios from 'axios';
import movieDetail from './components/movieDetail.vue';

const API_KEY = "api_key=3e21d0634b298df121ea5353d494ab2b";
const BASE_URL = 'https://api.themoviedb.org/3';
const API_URL = '/discover/movie?sort_by=popularity.desc&' + API_KEY;

export default {
  components: { movieDetail },
  name: 'App',
  compoents: {
    movieDetail,
  },
  data() {
    return {
      movies: [],

    }
  },

  created: function () { 
    this.loadData()
  },

  methods: {
    loadData() {
      axios.get(BASE_URL + API_URL)
        .then(response => this.movies = response.data.results)
        .catch(error => console.log(error))
    }
  }
}

</script>

<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 10px;
}

</style>