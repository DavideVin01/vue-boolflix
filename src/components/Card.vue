<template>
  <ul>
    <li>
      <img
        :src="`https://image.tmdb.org/t/p/w342${item.poster_path}`"
        :alt="item.title || item.name"
      />
      <h5>Titolo: {{ item.title || item.name }}</h5>
      <h6>Titolo originale: {{ item.original_title || item.original_name }}</h6>
      <div>
        Lingua originale:
        <img class="flag" v-if="hasFlag" :src="flagSrc" alt="" />
        <span class="text-uppercase" v-else
          ><strong>{{ item.original_language }}</strong></span
        >
      </div>
      <!-- <div>Voto: {{ this.vote_average }}</div> -->
      <span>Voto:</span>
      <span class="ms-1">
        <i
          v-for="(star, index) in stars"
          :key="index"
          class="fa-solid fa-star"
        ></i>
        <i
          v-for="(fullStar, index) in fullStars"
          :key="index"
          class="fa-regular fa-star"
        ></i>
      </span>
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
      totalStars: 5,
    };
  },
  computed: {
    hasFlag() {
      return this.flags.includes(this.item.original_language);
    },
    flagSrc() {
      return require(`../assets/img/${this.item.original_language}.png`);
    },
    stars() {
      return Math.ceil(this.item.vote_average / 2);
    },
    fullStars() {
      return this.totalStars - this.stars;
    },
  },
};
</script>

<style>
.flag {
  width: 35px;
  height: auto;
}
li {
  list-style-type: none;
}
.fa-star {
  color: rgb(255, 66, 66);
  filter: drop-shadow(0px 5px 2px rgba(0 0 0 / 0.1));
}
</style>