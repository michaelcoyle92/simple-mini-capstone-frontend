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
  methods: {},
};
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <p>Name:</p>
    <p>Description</p>
    <p></p>

    <div v-for="product in products" v-bind:key="product.id">
      {{ product.title }}
  </div>
</template>

<style></style>
