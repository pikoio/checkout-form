<script setup>
  import {inject} from "vue";
  import ProductItem from "@/components/ProductItem.vue";
  defineEmits(["remove-product-from-cart"]);
  const state = inject("state");
</script>

<template>
  <div class="products-list">
    <p class="header">My cart</p>
      <ProductItem
          v-for="product in state.products"
          :key="product.id"
          :product="product"
          @remove-product-from-cart="$emit('remove-product-from-cart', product.id)"
      />
  </div>
</template>

<style scoped>
  .products-list {
    width: 30%;
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