<template>
<div>
  <navBar />
  <movieDetail />

  <h2>Popular movies</h2>

  <div class="container">
    <div class="row align-items-center">
      <div class="col">
        <ul>
          <li v-for="movie of movies" :key="movie.id" @click="movie.showDetail = !movie.showDetail">
            <img  v-bind:src="'https://image.tmdb.org/t/p/w500' + movie.poster_path "  v-bind:alt="movie.title" class="img-responsive">
            <h3 v-show="movie.showDetail">{{ movie.title }}</h3>
            <p v-show="movie.showDetail">{{ movie.overview }}</p>
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
    // The Following Example is just similar to your one.
    // I defined an object test0 with moviesDetail array with one element 'false'
    // Please open a debug console to have a look. You can right click the page and select "inspect"
    let test0 = { moviesDetail: [ false ] }
    console.log('test0 result')
    console.log(!test0.moviesDetail)
    // I defined an object test0 with moviesDetail array with one element 'true'
    let test1 = { moviesDetail: [ true ] }
    console.log('test1 result')
    console.log(!test1.moviesDetail)

    this.loadData()
  },

  methods: {
    loadData() {
      axios.get(BASE_URL + API_URL)
        .then(response => {
          this.movies = response.data.results
          for (let i = 0; i < this.movies.length; i++) {
            // This is really javascript features only.
            // It will add extra field to movie object at any time without restriction
            // Don't do it Java or any other strong type Language
            // Strong type means Variable Type must be will define at compile time
            // Non-Strong type like Javascript, you can change the variable type at any time.
            this.movies[i].showDetail = false
          }
        })
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