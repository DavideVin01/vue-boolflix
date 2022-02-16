<template>
  <ul>
    <li>
      <div class="img-box">
        <img :src="posterPath" :alt="item.title || item.name" />
      </div>
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
      flags: ["it", "en", "fr", "es", "de", "ja", "hi", "tl"],
      totalStars: 5,
      images: {
        baseUri: "https://image.tmdb.org/t/p/w342",
        placeholder:
          "https://www.altavod.com/assets/images/poster-placeholder.png",
      },
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
    posterPath() {
      if (!this.item.poster_path) return this.images.placeholder;
      return this.images.baseUri + this.item.poster_path;
    },
  },
};
</script>

<style lang="scss">
.flag {
  width: 35px;
  height: auto;
}
ul:hover {
  background-color: rgba(#000, 0.5);
}
li {
  list-style-type: none;
}
.img-box {
  width: 342px;
}
img:hover {
  background-color: rgba(#000, 0.5);
}
.fa-star {
  color: rgb(255, 66, 66);
  filter: drop-shadow(0px 5px 2px rgba(0 0 0 / 0.1));
}
</style>