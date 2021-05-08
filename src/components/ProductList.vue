<template>
  <section>
    <div v-for="(item, index) in products" :key="index">
      <ProductItem :product="item" />
    </div>
    <p><b>Total:</b>{{ totalProducts }} produtos</p>
  </section>
</template>

<script>
import ProductItem from "./ProductItem";

export default {
  name: "ProductList",
  components: {
    ProductItem,
  },
  props: {
    products: Array,
  },
  data() {
    return {};
  },
  computed: {
    totalProducts: function () {
      const total = this.products.length;

      return ` ${total}`;
    },
  },
};
</script>

<style scoped>
section {
  background-color: #52616f;
  border: 1px solid #52616f;
  padding-bottom: 5px;
  border-radius: 5px;
}

section p {
  font-weight: bold;
  color: #f0a500;

  float: right;
}
b {
  color: #52616f;
}
div {
  padding: 5px;
}
</style>