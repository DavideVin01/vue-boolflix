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
      films: [],
      tvSeries: [],
      placeholder: "Cerca un film o una serie TV",
      api: {
        language: "it-IT",
        baseUri: "https://api.themoviedb.org/3",
        api_key: "d6c46c53bff219eb5ef0e2f7c5b73130",
      },
    };
  },
  methods: {
    fetchFilms(query) {
      if (!query) {
        this.films = [];
        this.tvSeries = [];
        return;
      }
      const config = {
        params: {
          query,
          api_key: this.api.api_key,
          language: this.api.language,
        },
      };
      this.fetchApi("search/movie", config, "films");
      this.fetchApi("search/tv", config, "tvSeries");
    },
    fetchApi(endpoint, config, target) {
      axios.get(`${this.api.baseUri}/${endpoint}`, config).then((res) => {
        this[target] = res.data.results;
      });
    },
  },
};
</script>

<style lang="scss">
@import "./assets/scss/style.scss";
</style>
