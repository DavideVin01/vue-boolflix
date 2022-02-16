<template>
  <header>
    <div class="d-flex justify-content-between bg-dark p-2 align-items-center">
      <div>
        <span id="boolfix" class="h1 text-danger">BOOLFIX</span>
      </div>
      <div class="d-flex align-items-center">
        <input
          class="me-2 rounded"
          type="text"
          v-model="query"
          :placeholder="placeholder"
          @keyup.enter="emitSearch(query)"
        />
        <button class="btn btn-danger" @click="emitSearch(query)">Cerca</button>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  props: ["placeholder"],
  data() {
    return {
      query: "",
    };
  },
  methods: {
    emitSearch(query) {
      return this.$emit("searched", query);
    },
  },
};
</script>

<style scoped lang="scss">
header {
  filter: drop-shadow(0px 4px 0px #000000);
}

input {
  width: 500px;
  border: 0;
  filter: drop-shadow(0px 4px 0px #5c5c5c);
  &:focus {
    outline: 0px;
  }
}

#boolfix,
button {
  filter: drop-shadow(0px 4px 0px #660000);
}
</style>