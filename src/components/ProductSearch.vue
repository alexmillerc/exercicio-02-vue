<template>
  <div>
    <input
      type="text"
      placeholder="Buscar"
      v-model="search"
      v-on:keyup="handleSearch"
    />
  </div>
</template>

<script>
export default {
  name: "ProductSearch",
  components: {},
  props: {
    onSearch: Function,
  },
  data() {
    return {
      search: "",
    };
  },
  methods: {
    handleSearch() {
      this.onSearch(this.search);
    },
  },
};
</script>

<style scoped>
input {
  padding: 10px;
  margin-bottom: 2%;
  border: 1px solid #f0a500;
  border-radius: 5px;
  color: #52616f;
}
textarea:focus,
input:focus {
  box-shadow: 0 0 0 0;
  outline: 0;
}
</style>