<template>
  <main>
    <div class="ms-2" v-if="films.length && tvSeries.length">
      <section id="films">
        <h3>Film</h3>
        <Card v-for="film in films" :key="film.id" :item="film" />
      </section>
      <section id="tv-series">
        <h3>Serie TV</h3>
        <Card v-for="serie in tvSeries" :key="serie.id" :item="serie" />
      </section>
    </div>
    <h2 v-else class="ms-2">Cerca un film o una serie TV</h2>
  </main>
</template>

<script>
import Card from "./Card.vue";
export default {
  name: "Main",
  props: ["films", "tvSeries"],
  components: {
    Card,
  },
};
</script>

<style>
</style>