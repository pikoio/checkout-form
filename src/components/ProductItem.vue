<script setup>
defineProps(["product"]);
</script>

<template>
  <div class="product-item">
    <div class="row-1">
      <p class="name">{{ product.name }}</p>
      <button class="remove-btn"><i class="pi pi-trash"></i></button>
    </div>
    <p class="price">{{ product.price }}$</p>
  </div>
</template>

<style scoped>
  .product-item{
    height: 5rem;
    padding: 1rem;
    background-color: #e8f4e8;
    color: #3d6138;
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
    background-color: #54a852;
    color: #fff;
    cursor: pointer;
  }
  .product-item .row-1 .remove-btn:hover{
    background-color: #3e9a3d;
  }
</style>