<template>
  <main>
    <ul v-if="films.length && tvSeries.length">
      <h3>Film</h3>
      <li v-for="film in films" :key="film.id">
        <h5>Titolo: {{ film.title }}</h5>
        <h6>Titolo originale: {{ film.original_title }}</h6>
        <div>
          Lingua originale:
          <span v-if="film.original_language === 'en'"
            ><img class="flag" src="../assets/img/en.png" alt="English Flag"
          /></span>
          <span v-else-if="film.original_language === 'it'"
            ><img
              class="flag"
              src="../assets/img/it.png"
              alt="Bandiera Italiana"
          /></span>
          <span v-else-if="film.original_language === 'de'"
            ><img
              class="flag"
              src="../assets/img/de.png"
              alt="Bandiera Tedesca"
          /></span>
          <span v-else-if="film.original_language === 'fr'"
            ><img
              class="flag"
              src="../assets/img/fr.png"
              alt="Bandiera Francese"
          /></span>
          <span v-else-if="film.original_language === 'es'"
            ><img
              class="flag"
              src="../assets/img/es.png"
              alt="Bandiera Spagnola"
          /></span>
          <span class="text-uppercase" v-else
            ><strong>{{ film.original_language }}</strong></span
          >
        </div>
        <div>Voto: {{ film.vote_average }}</div>
      </li>
      <h3>Serie TV</h3>
      <li v-for="serie in tvSeries" :key="serie.id">
        <h5>Titolo: {{ serie.name }}</h5>
        <h6>Titolo originale: {{ serie.original_name }}</h6>
        <div>
          Lingua originale:
          <span v-if="serie.original_language === 'en'"
            ><img class="flag" src="../assets/img/en.png" alt="English Flag"
          /></span>
          <span v-else-if="serie.original_language === 'it'"
            ><img
              class="flag"
              src="../assets/img/it.png"
              alt="Bandiera Italiana"
          /></span>
          <span v-else-if="serie.original_language === 'de'"
            ><img
              class="flag"
              src="../assets/img/de.png"
              alt="Bandiera Tedesca"
          /></span>
          <span v-else-if="serie.original_language === 'fr'"
            ><img
              class="flag"
              src="../assets/img/fr.png"
              alt="Bandiera Francese"
          /></span>
          <span v-else-if="serie.original_language === 'es'"
            ><img
              class="flag"
              src="../assets/img/es.png"
              alt="Bandiera Spagnola"
          /></span>
          <span v-else class="text-uppercase"
            ><strong>{{ serie.original_language }}</strong></span
          >
        </div>
        <div>Voto: {{ serie.vote_average }}</div>
      </li>
    </ul>
    <h2 v-else class="ms-2">Cerca un film o una serie TV</h2>
  </main>
</template>

<script>
export default {
  name: "Main",
  props: ["films", "tvSeries"],
};
</script>

<style>
.flag {
  width: 35px;
  height: auto;
}
</style>