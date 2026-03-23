<script setup>

defineProps(["product"]);
defineEmits(["remove-product-from-cart", "add-product-to-cart"])
</script>

<template>
  <div
      class="product-card"
      :style="{ backgroundColor: product.cardColor }">
    <div
        class="header-row"
        :style="{ color: product.cardColor }">
      <p>{{ product.name}}</p>
    </div>
    <div class="menu-row">
      <template v-if="!product.isInState">
        <button
            class="buy-btn"
            @click="$emit('add-product-to-cart')">
          Buy now
        </button>
        <button
            class="add-to-cart-btn"
            @click="$emit('add-product-to-cart')">
          Add to cart
        </button>
      </template>
      <button v-else class="remove-from-cart-btn">Remove from cart</button>
    </div>
  </div>
</template>

<style scoped>
  .product-card {
    height: 30rem;
    width: 25rem;
    background-color: var(--color-pale-green);
    border-radius: 0.5rem;
    box-shadow: var(--box-shadow);
    padding: 2.5rem 2.5rem 2.5rem 0;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    transition: height 0.5s, width 0.5s;
  }
  .product-card:hover{
    height: 31rem;
    width: 26rem;
  }
  .product-card .header-row {
    background-color: var(--color-white);
    height: 8rem;
    box-shadow: var(--box-shadow);
    border-radius: 0 0.5rem 0.5rem 0;
    padding: 2.5rem;
    display: flex;
    align-items: center;
    color: var(--color-pale-green);
    font-size: 2.7rem;
  }
  .product-card .menu-row {
    margin-left: 2.5rem;
    height: 5rem;
    display: flex;
    justify-content: center;
  }
  .product-card .menu-row button{
    height: 100%;
    font-size: 1.2rem;
    vertical-align: middle;
  }
  .product-card .menu-row .buy-btn {
    width: 50%;
    background-color: var(--color-btn-1);
    color: var(--color-white);
    border-radius: 0.5rem;
    transition: background-color 0.5s;
    box-shadow: var(--box-shadow);
  }
  .product-card .menu-row .buy-btn:hover{
    background-color: var(--color-btn-1-hover);
  }
  .product-card .menu-row .add-to-cart-btn {
    width: 50%;
    background-color: transparent;
    color: var(--color-white);
    transition: color 0.3s;
  }
  .product-card .menu-row .add-to-cart-btn:hover {
    color: var(--color-grey);
  }
  .product-card .menu-row .remove-from-cart-btn {
    background-color: transparent;
    color: var(--color-white);
    transition: color 0.3s;
    font-size: 1.3rem;
  }
  .product-card .menu-row .remove-from-cart-btn:hover {
    color: var(--color-grey);
  }


</style>