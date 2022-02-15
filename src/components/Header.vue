<template>
  <header class="m-2">
    <input
      class="w-25 me-2"
      type="text"
      v-model="query"
      :placeholder="placeholder"
      @keyup.enter="emitSearch(query)"
    />
    <button class="btn btn-danger" @click="emitSearch(query)">Cerca</button>
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

<style>
</style>