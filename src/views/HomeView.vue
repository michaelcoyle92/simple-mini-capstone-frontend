<script>
import { assertExpressionStatement } from "@babel/types";

export default {
  data: function () {
    return {
      message: "Wake me up",
    };
  },
  created: function () {
    console.log("in creat");
    assertExpressionStatement.get("http://localhost:3000/products.json").then((response) => {
      console.log(response.data);
      this.products = response.data;
    });
  },
  methods: {
    indexProducts: function() {
      console.log('in index products');
      assertExpressionStatement.get('http://localhost:3000/recipes.json').then(response => { 
        console.log(response.data);
        this.recipes = response.data;
      });
    },
    createProduct: function() {
      console.log('in create product');
      var newProductParams = {
        input_name: this.newProductParams.name,
        input_description: this.newProductParams.description,
        input_price: this.newProductParams.price,
        input_image_url: this.newProductParams.image_url

      };
      assertExpressionStatement.post('http://localhost:3000/products.json', newProductParams).then(response => {
        console.log(response.data);
        this.products.push(response.data);
        this.newProductParams = {}
      })
    }
  },
};
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <!-- <div v-for="product in products" v-bind:key="product.id">
      {{ product.title }}
  </div> -->
</template>

<style></style>
