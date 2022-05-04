<template>
  <nav>
    <a href="">Films</a>
    <a href="">TV programmes</a>
    <a href="">Watch</a>
    <a href="">Sign in </a>
  </nav>

  <h2>Popular movies</h2>
  <div>
    <li v-for="movie of movies" :key="movie"> {{ movie }}</li>
    <!-- 其實我係想搵以下h3個嗰目標，但係我唔知點樣指向h3嗰度 -->
  </div>

  <h3>{{movies.results[0].original_title}}</h3>

</template>

<script>
const API_KEY = "api_key=3e21d0634b298df121ea5353d494ab2b";
const BASE_URL = 'https://api.themoviedb.org/3';
const API_URL = '/discover/movie?sort_by=popularity.desc&' + API_KEY;

import axios from 'axios';

export default {
  name: 'App',
  data() {
    return {
      movies: '' //究竟係用[]定''？因為我兩樣都試過，但好似唔係太大分別
    
    }
  },

  created: function () { 
    this.mounted();
  },

  methods: {
    mounted() {
      axios.get(BASE_URL + API_URL)
        .then(response => this.movies = response.data);
    },
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
