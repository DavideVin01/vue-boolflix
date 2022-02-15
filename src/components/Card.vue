<template>
  <ul>
    <li>
      <img :src="`https://image.tmdb.org/t/p/w342${item.poster_path}`" alt="" />
      <h5>Titolo: {{ item.title || item.name }}</h5>
      <h6>Titolo originale: {{ item.original_title || item.original_name }}</h6>
      <div>
        Lingua originale:
        <img class="flag" v-if="hasFlag" :src="flagSrc" alt="" />
        <span class="text-uppercase" v-else
          ><strong>{{ item.original_language }}</strong></span
        >
      </div>
      <div>Voto: {{ item.vote_average }}</div>
    </li>
  </ul>
</template>

<script>
export default {
  name: "Card",
  props: ["item"],
  data() {
    return {
      flags: ["it", "en", "fr", "es", "de"],
    };
  },
  computed: {
    hasFlag() {
      return this.flags.includes(this.item.original_language);
    },
    flagSrc() {
      return require(`../assets/img/${this.item.original_language}.png`);
    },
  },
};
</script>

<style>
.flag {
  width: 35px;
  height: auto;
}
</style>