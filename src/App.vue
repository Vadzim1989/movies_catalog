<template>
  <div class="movies_catalog">
    <Navigation/>
    <p v-if="filterMovies.length">You searched for: {{filterMovies}}, {{movies.totalResults}} results found</p>
    <div class="movies_wrapper">
      <Movies 
        v-bind:movies="movies"
        v-for="movies in movies.Search" :key="movies.imdbID"/>
    </div>
    <Pagination v-if="filterMovies"/>
  </div>
</template>

<script>
import Navigation from './components/Navigation.vue';
import Movies from './components/Movies.vue';
import Pagination from './components/Pagination.vue'

export default {
  name: 'App',
  data() {
    return {
      movies: [],
      filterMovies: '',
      page: 1
    }
  },
  components: {
    Navigation,
    Movies,
    Pagination
  },
  methods: {
    getMovies() {
      fetch(`https://www.omdbapi.com/?i=tt3896198&apikey=8523cbb8&s=${this.filterMovies}`)
      .then(res => res.json())
      .then(json => {
        this.movies = json;
        this.page = 1;
        })
    },
    getMoviesPage() {
      fetch(`https://www.omdbapi.com/?i=tt3896198&apikey=8523cbb8&s=${this.filterMovies}&page=${this.page}`)
      .then(res => res.json())
      .then(json => {
        this.movies = json
        })
    }
  },
  created() {
    this.$on('page-down', () => {
      if(this.page === 1){
        this.page;
      } else {
        this.page--;
      }
    });
    this.$on('page-up', () => {
      this.page++;
    })
  },
  watch: {
    'filterMovies': 'getMovies',
    'page': 'getMoviesPage'
  }
}
</script>

<style>
body {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.movies_wrapper {
  display: flex;
  flex-flow: row wrap;
  justify-content: space-around;
}
</style>
