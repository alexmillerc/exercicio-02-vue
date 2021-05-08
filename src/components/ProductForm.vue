<template>
  <div>
    <form @submit.prevent="onFormSubmit">
      <p>Cadastro de Produtos</p>
      <input type="text" placeholder="Nome" v-model="name" required />
      <input type="number" placeholder="Preço" v-model="price" required />
      <input type="text" placeholder="Categoria" v-model="category" required />
      <input type="submit" value="Cadastrar" />
    </form>
  </div>
</template>

<script>
export default {
  name: "ProductForm",
  data() {
    return {
      name: "",
      price: "",
      category: "",
    };
  },
  props: {
    onAddProduct: Function,
  },
  methods: {
    onFormSubmit() {
      const product = {
        name: this.name,
        price: this.price,
        category: this.category,
      };
      this.onAddProduct(product);
      this.name = "";
      this.price = "";
      this.category = "";
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  background-color: #52616f;
  border-radius: 5px;
  padding: 10px 60px 40px;
  width: 300px;
}
form p {
  color: #fdfdfe;
  font-size: x-large;
  font-weight: bold;
  text-align: center;
}
input {
  margin: 1%;
  line-height: 20px;
  padding: 10px;
  font-size: larger;
  border-radius: 5px;
  border: none;
}

input[type="submit"] {
  background-color: #f0a500;
  color: #52616f;
  border-radius: 5px;
  font-weight: bold;
  font-size: larger;
}
textarea:focus,
input:focus {
  box-shadow: 0 0 0 0;
  outline: 0;
}
</style>