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
            v-moodel="term"
          />
          <button
            class="btn btn-outline-secondary"
            type="button"
            @click="search"
          >
            Cerca
          </button>
        </div>
      </div>
    </header>
  </div>
</template>

<script>
export default {
  name: "App",

  data() {
    return {
      movies: [],
      term: "",
    };
  },
  methods: {
    search() {
      console.log("Ciao");
    },
  },
};
</script>

<style lang="scss">
@import "./assets/sass/style.scss";
</style>
