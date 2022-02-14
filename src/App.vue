<template>
  <div id="boolfix">
    <Header @searched="fetchFilms" :placeholder="placeholder" />
    <Main :films="films" :tvSeries="tvSeries" />
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      api_key: "d6c46c53bff219eb5ef0e2f7c5b73130",
      films: [],
      tvSeries: [],
      placeholder: "Cerca un film o una serie TV",
    };
  },
  methods: {
    fetchFilms(query) {
      const config = {
        params: {
          query: query,
          api_key: this.api_key,
          language: "it-IT",
        },
      };

      axios
        .get(`https://api.themoviedb.org/3/search/movie`, config)
        .then((res) => {
          this.films = res.data.results;
        });

      axios
        .get(`https://api.themoviedb.org/3/search/tv`, config)
        .then((res) => {
          this.tvSeries = res.data.results;
        });
    },
  },
};
</script>

<style lang="scss">
</style>
