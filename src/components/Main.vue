<template>
  <main class="py-2">
    <div v-if="films.length && tvSeries.length">
      <section id="films">
        <h3 class="black-shadow title">Film</h3>
        <div id="film-container" class="d-flex flex-wrap">
          <Card v-for="film in films" :key="film.id" :item="film" />
        </div>
      </section>
      <section id="tv-series">
        <h3 class="black-shadow title">Serie TV</h3>
        <div id="series-container" class="d-flex flex-wrap">
          <Card v-for="serie in tvSeries" :key="serie.id" :item="serie" />
        </div>
      </section>
    </div>
    <h2 id="placeholder-title" v-else class="ms-3 black-shadow title">
      Cerca un film o una serie TV
    </h2>
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

<style scoped lang="scss">
.black-shadow {
  filter: drop-shadow(0px 1.5px 0px #000000);
}

.title {
  font-size: 54px;
  filter: drop-shadow(1px 3.5px 0px #000000);
  margin: 10px 0 0 37px;
}
</style>