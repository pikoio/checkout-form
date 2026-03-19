<script setup>
  import {inject} from "vue";
  import ProductCard from "@/components/ProductCard.vue";

  const products = inject("products")
</script>

<template>
  <div class="products-wrapper">
    <ProductCard v-for="product in products" :key="product.id" :product="product"/>
  </div>
</template>

<style scoped>
  .products-wrapper {
    display: flex;
    gap: 1rem;
    margin-top: 3rem;
    margin-bottom: 3rem;
  }
</style>