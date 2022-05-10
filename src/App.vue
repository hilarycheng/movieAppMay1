<template>
<div>
  <navBar />
  <movieDetail />

  <h2>Popular movies</h2>

  <div class="container">
    <div class="row align-items-center">
      <div class="col">
        <ul>
          <li v-for="movie of movies" :key="movie.id" @click="showDetail = !showDetail">
            <img  v-bind:src="'https://image.tmdb.org/t/p/w500' + movie.poster_path "  v-bind:alt="movie.title" class="img-responsive">
            <h3 v-show="showDetail">{{ movie.title }}</h3>
            <p v-show="showDetail">{{ movie.overview }}</p>
          </li>
        </ul>
      </div>
    </div>
  </div>
</div>

</template>

<script>
import axios from 'axios';
import navBar from './components/navBar.vue';
import movieDetail from './components/movieDetail.vue';

const API_KEY = "api_key=3e21d0634b298df121ea5353d494ab2b";
const BASE_URL = 'https://api.themoviedb.org/3';
const API_URL = '/discover/movie?sort_by=popularity.desc&' + API_KEY;

export default {
  name: 'App',
  components: {
    movieDetail,
    navBar,

  },
  data() {
    return {
      movies: [],
      showDetail: false,

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