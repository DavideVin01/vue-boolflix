<template>
  <header class="m-2">
    <input
      class="w-25 me-2"
      type="text"
      v-model="query"
      :placeholder="placeholder"
    />
    <button class="btn btn-danger" @click="$emit('searched', query)">
      Cerca
    </button>
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
};
</script>

<style>
</style>