<template>
  <div id="app">
    <header class="container d-flex justify-content-between align-items-center">
      <div>BOOLFLIX</div>
      <div>
        <div class="input-group mb-3">
          <input
            type="text"
            class="form-control"
            placeholder="Inserisci un titolo "
            v-model="term"
          />
          <button
            class="btn btn-outline-secondary"
            type="button"
            @click="fetchMovie"
          >
            Cerca
          </button>
        </div>
      </div>
    </header>
    <main>
      <div class="container">
        <div
          class="card"
          v-for="movie in movies"
          :key="movie.id"
          style="width: 18rem"
        >
          <div class="card-header">{{ movie.title }}</div>
          <ul class="list-group list-group-flush">
            <li class="list-group-item">{{ movie.original_title }}</li>
            <li class="list-group-item">{{ movie.original_language }}</li>
            <li class="list-group-item">{{ movie.vote_average }}</li>
          </ul>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "App",

  data() {
    return {
      movies: [],
      term: "",
      query: "Batman",
      api_key: "0a121df1225a21502274c82149935a89",
    };
  },

  methods: {
    genreList() {
      const genres = [];
      this.movies.forEach((movie) => {
        const { genre } = movie;
        if (!genres.includes(genre)) genres.push(genre);
      });
      return genres;
    },

    fetchMovie() {
      const config = {
        params: {
          api_key: this.api_key,
          query: this.query,
          language: "it-IT",
        },
      };
      axios
        .get(`https://api.themoviedb.org/3/search/movie`, config)
        .then((res) => {
          this.movies = res.data.results;

          this.genreList();
        });
    },
  },
};
</script>

<style lang="scss">
@import "./assets/sass/style.scss";
</style>
