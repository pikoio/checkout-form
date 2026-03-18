<script setup>
  import ProductsWrapper from "@/components/ProductsWrapper.vue";
  import {provide, ref} from "vue";

  const products = ref([
    {
      id: 1,
      name: "Grape juice",
      description: "Grape juice from USA",
      price: 10,
      cardColor: "#805a98"
    },
    {
      id: 2,
      name: "Apple juice",
      description: "Apple juice from China",
      price: 20,
      cardColor: "#ba4e4e"
    },
    {
      id: 3,
      name: "Orange juice",
      description: "Orange juice from Japan",
      price: 30,
      cardColor: "#d68348"
    }
  ])
  provide("products", products)

</script>

<template>
  <div class="container">
    <div class="nav-bar">
      <p class="logo">Juices shop</p>
      <button class="my-cart-btn">My cart</button>
    </div>
    <ProductsWrapper/>
  </div>
</template>

<style scoped>
  .container {
    border: 1px solid red;
    display: flex;
    flex-direction: column;
    align-items: center;

  }
  .container .nav-bar {
    border: 1px solid black;
    height: 4rem;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .container .nav-bar .logo{
    font-size: 2rem;
  }
  .container .nav-bar .my-cart-btn{
    height: 4rem;
    width: 4rem;
  }
</style>
