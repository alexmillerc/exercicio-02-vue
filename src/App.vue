<template>
  <div class="container">
    <ProductForm :onAddProduct="handleOnAddProduct"/>
    <div class="box">
      <ProductSearch :onSearch="handleSearchProducts"/>    
      <ProductList :products="listedProducts.length > 0 ? listedProducts : products"/>
    </div>
  </div>
</template>

<script>
import ProductForm from './components/ProductForm';
import ProductList from './components/ProductList';
import ProductSearch from './components/ProductSearch';

export default {
  name: 'App',
  components: {
    ProductForm,
    ProductList,
    ProductSearch,
  },
  data(){
    return{
      products: [],
      listedProducts: [],
    }
  },
  methods: {
    handleOnAddProduct(product){
      this.products = this.products.concat(product);
    },
    handleSearchProducts(text){
      const results = this.products.filter((e) => e.name.startsWith(text));
      if(results.length > 0){
        this.listedProducts = results;
      } else{
        this.listedProducts = this.products;
      }
    }
  }
}
</script>

<style scoped>
  .container{
    display: flex;
    justify-content: space-evenly;
  }
</style>
