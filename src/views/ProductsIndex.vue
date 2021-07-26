<template>
  <div class="products-index">
    <h1>All Products</h1>
    <div v-for="product in products" :key="product.id">
      <h2>Name: {{ product.name }}</h2>
      <p>Description: {{ product.description }}</p>
      <img v-bind:src="product.image_url" alt="product.title" />
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      products: [],
    };
  },
  created: function () {
    this.indexProducts();
  },
  methods: {
    indexProducts: function () {
      axios.get("/products").then((response) => {
        this.products = response.data;
        console.log("All products:", this.products);
      });
    },
  },
};
</script>
