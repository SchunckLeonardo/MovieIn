<template>
  <div class="mt-5 container">
    <div class="row">
      <h1 class="col-lg-12 display-2 text-light border-bottom">
        Lista de filmes
      </h1>
    </div>
    <div class="row d-flex justify-content-center">
      <moviesCard
        class="m-5"
        v-for="movie in movies"
        :key="movie.id"
        :title="movie.title"
        :poster="`https://image.tmdb.org/t/p/w500${movie.poster_path}`"
      />
    </div>
    <div class="row">
      <div class="col-lg-12 d-flex justify-content-center p-5">
        <button class="btn btn-warning me-auto" v-show="prev" @click="prevPage">
          Anterior
        </button>
        <h3 class="text-light">Página {{ currentPage }}</h3>
        <button class="btn btn-warning ms-auto" v-show="next" @click="nextPage">
          Próxima
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import moviesCard from "./moviesCard";
import axios from "axios";

export default {
  components: {
    moviesCard,
  },
  data() {
    return {
      currentPage: 1,
      movies: [],
      next: true,
      prev: false,
    };
  },
  created() {
    this.getAllMovies();
  },
  watch: {
    currentPage() {
      this.getAllMovies();
    },
  },
  methods: {
    prevPage() {
      this.currentPage -= 1;
      this.updateButtonVisibility();
      window.scrollTo(0, 0);
    },
    nextPage() {
      this.currentPage += 1;
      this.updateButtonVisibility();
      window.scrollTo(0, 0);
    },
    updateButtonVisibility() {
      this.prev = this.currentPage > 1;
      this.next = this.currentPage < 500;
    },
    getAllMovies() {
      let apiKey = "7cd63b93d7a9030a8da1c345b1fb3221";
      axios
        .get(
          `https://api.themoviedb.org/3/movie/popular?api_key=${apiKey}&language=pt-BR&page=${this.currentPage}`
        )
        .then((response) => {
          this.movies = response.data.results;
          this.next = response.data.page < response.data.total_pages;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style>
</style>