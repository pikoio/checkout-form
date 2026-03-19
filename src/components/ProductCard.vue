<script setup>
defineProps(["product"]);

</script>

<template>
  <div
      class="product-card"
      :style="{ backgroundColor: product.cardColor}">
    <p class="name">{{ product.name }}</p>
    <p class="description">{{ product.description }}</p>
    <p class="price">{{ product.price }}$</p>
    <div class="btn-menu">
      <button class="buy-btn">Buy</button>
      <button class="add-cart-btn">Add to cart</button>
    </div>
  </div>
</template>

<style scoped>
  .product-card {
    height: 18rem;
    width: 15rem;
    background-color: #b3b3b3;
    padding: 1.5rem;
    display: flex;
    flex-direction: column;
    color: white

  }
  .product-card .name{
    font-size: 2rem;
  }
  .product-card .description {
    font-size: 1rem;
  }
  .product-card .price{
    font-size: 3rem;
    margin-top: 1rem;
  }
  .product-card .btn-menu{
    margin-top: 1.5rem;
    flex: 1;
    display: flex;
    justify-content: space-between;
  }
  .product-card .btn-menu button{
    width: 50%;
    border: none;
    cursor: pointer;
  }
  .product-card .btn-menu .buy-btn{
    background-color: #56aa54;
    color: #ffffff;
  }
  .product-card .btn-menu .buy-btn:hover{
    background-color: #3e9a3d;
  }
  .product-card .btn-menu .add-cart-btn:hover{
    background-color: #efefef;
  }
</style>