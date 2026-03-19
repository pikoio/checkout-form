<script setup>
  import {inject} from "vue";
  import ProductItem from "@/components/ProductItem.vue";

  const state = inject("state");
</script>

<template>
  <div class="products-list">
    <p class="header">My cart</p>
    <ProductItem v-for="product in state.products" :key="product.id" :product="product"/>
  </div>
</template>

<style scoped>
  .products-list {
    width: 35%;
    display: flex;
    flex-direction: column;
    gap: 1rem;
    overflow: auto;
    padding: 1rem;
  }
  .products-list .header{
    font-size: 1.4rem;
  }
</style>