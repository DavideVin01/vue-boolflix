<template>
  <main>
    <ul>
      <h3>Film</h3>
      <li v-for="film in films" :key="film.id">
        <h5>Titolo: {{ film.title }}</h5>
        <h6>Titolo originale: {{ film.original_title }}</h6>
        <p>
          Lingua: {{ film.original_language }}
          <br />
          Voto: {{ film.vote_average }}
        </p>
      </li>
      <h3>Serie TV</h3>
      <li v-for="serie in tvSeries" :key="serie.id">
        <h5>Titolo: {{ serie.name }}</h5>
        <h6>Titolo originale: {{ serie.original_name }}</h6>
        <p>
          Lingua: {{ serie.original_language }}
          <br />
          Voto: {{ serie.vote_average }}
        </p>
      </li>
    </ul>
  </main>
</template>

<script>
export default {
  name: "Main",
  props: ["films", "tvSeries"],
};
</script>

<style>
</style>