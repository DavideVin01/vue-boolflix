<template>
  <div id="boolfix">
    <Header />
    <Main />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";
export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  // methods: {
  //   fetchMovies() {},
  // },
};
</script>

<style lang="scss">
</style>
