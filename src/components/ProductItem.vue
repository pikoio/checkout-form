<script setup>
defineProps(["product"]);
defineEmits(["remove-product-from-cart"]);
</script>

<template>
  <div class="product-item">
    <div class="row-1">
      <p class="name">{{ product.name }}</p>
      <button
          @click="$emit('remove-product-from-cart')"
          class="remove-btn">
        <i class="pi pi-trash"></i>
      </button>
    </div>
    <p class="price">{{ product.price }}$</p>
  </div>
</template>

<style scoped>
  .product-item{
    height: 5rem;
    padding: 1rem;
    background-color: var(--color-pale-green);
    color: var(--color-text);
    display: flex;
    flex-direction: column;
  }
  .product-item .row-1{
    font-size: 1rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .product-item .row-1 .remove-btn{
    height: 1.5rem;
    width: 1.5rem;
    display: flex;
    align-items: center;
    justify-content: center;
    border: none;
    background-color: var(--color-btn-1);
    color: var(--color-white);
    cursor: pointer;
  }
  .product-item .row-1 .remove-btn:hover{
    background-color: var(--color-btn-1-hover);
  }
</style>