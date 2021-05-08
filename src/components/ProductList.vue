<template>
  <section>
    <ProductSearch :onSearch="handleSearchProducts"/>
    <div class="box">
      <div v-if="listedProducts.length > 0">
        <div v-for="(item, index) in listedProducts" :key="index">
          <ProductItem :product="item" />
        </div>
      </div>
      <div v-else>
        <div v-for="(item, index) in products" :key="index">
          <ProductItem :product="item" />
        </div>
        <p><b>Total:</b>{{ totalProducts }} produtos</p>
      </div>
    </div>
    
    <button><router-link to="/">Home</router-link></button>
  </section>
</template>

<script>
import ProductItem from "./ProductItem";
import ProductSearch from './ProductSearch';

export default {
  name: "ProductList",
  components: {
    ProductItem,
    ProductSearch,
  },
  props: {
  },
  data(){
    return{
      products: this.$store.getters.getProducts,
      listedProducts: [],
    }
  },
  methods: {
    handleSearchProducts(text){
      const results = this.products.filter((e) => e.name.startsWith(text));
      if(results.length > 0){
        this.listedProducts = results;
      } else {
        this.listedProducts = this.products;
      }
    }
  },
  computed: {
    totalProducts: function(){
      const products = this.$store.state.products.length;
      const listedProducts = this.listedProducts.length;
      const total = listedProducts > 0 ? listedProducts : products;
      return total > 1 || total === 0 ? ` ${total}` : ` ${total}`;
    },
  },
};
</script>


<style scoped>
section {
  width: 300px;
  background-color: #52616f;
  border: 1px solid #52616f;
  padding-bottom: 5px;
  border-radius: 5px;
}

.box div{
  background-color: #52616f;;
}

section p{
  font-weight: bold;
  color: #fdfdfe;
  float: right;
}
b {
  color: #f0a500;
}

div {
  padding: 5px
}

button{
  background-color: #f0a500;
  color: #52616f;
  border-radius: 5px;
  font-weight: bold;
  font-size: larger;
  margin: 2%;
  width: 290px;
  line-height: 10px;
  padding: 15px;
  border-radius: 5px;
  border: none;
}

a {
  text-decoration: none;
  display: flex;
  justify-content: center;
  font-weight: bold;
  font-size: large;
  color: #52616f;
}


</style>