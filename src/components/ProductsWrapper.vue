<script setup>
import {computed, inject} from "vue";
  import ProductCard from "@/components/ProductCard.vue"

  defineEmits(["remove-product-from-cart", "add-product-to-cart"])

  const products = inject("products")
  const state = inject("state")

</script>

<template>
  <div class="products-wrapper">
    <ProductCard
        v-for="product in products"
        :key="product.id"
        :product="product"
        @remove-product-from-cart="$emit('remove-product-from-cart', product.id)"
        @add-product-to-cart="$emit('add-product-to-cart', product.id)"
        />
  </div>
</template>

<style scoped>
  .products-wrapper {
    display: flex;
    gap: 2rem;
    margin-top: 3rem;
    margin-bottom: 3rem;
  }
</style>