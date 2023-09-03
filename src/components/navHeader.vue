<template>
  <nav class="navbar navbar-expand-lg bg-body-tertiary">
    <div class="container-fluid px-5 py-3">
      <a class="navbar-brand" href="#"
        ><i class="bi bi-film text-warning"></i> Leo MoviesLab</a
      >
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-5 mb-2 mb-lg-0 ms-auto">
          <li class="nav-item">
            <a class="nav-link" aria-current="page" href="#">Todos os filmes</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Categorias</a>
          </li>
        </ul>
        <form class="d-flex" role="search">
          <input
            class="form-control me-2"
            type="search"
            placeholder="Search"
            aria-label="Search"
            v-model="search"
          />
          <button class="btn btn-outline-success" type="submit" @click="searchMovie($event)">Search</button>
        </form>
      </div>
    </div>
  </nav>
</template>

<script>
import axios from "axios";

export default {
  methods: {
    searchMovie(event) {
      event.preventDefault();
      const options = {
        method: "GET",
        url: "https://api.themoviedb.org/3/search/movie",
        params: {
          query: `${this.search}`,
          include_adult: "false",
          language: "pt-BR",
          page: "1",
        },
        headers: {
          accept: "application/json",
          Authorization:
            "Bearer eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiI3Y2Q2M2I5M2Q3YTkwMzBhOGRhMWMzNDViMWZiMzIyMSIsInN1YiI6IjY0ZWY3ZWEyZGJiYjQyMDEzYTIyNDk2MiIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.YXOe4lOgCTMXgz04ryaNnHgFStePGHu9PJH84K0heA4",
        },
      };

      axios
        .request(options)
        .then(function (response) {
          console.log(response.data.results);
        })
        .catch(function (error) {
          console.error(error);
        });
    },
  },
  data() {
    return {
      search: "",
    };
  },
};
</script>

<style>
</style>