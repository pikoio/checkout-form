<script setup>
  import ProductsWrapper from "@/components/ProductsWrapper.vue";
  import {provide, ref} from "vue";
  import CartSection from "@/components/CartSection.vue";
  const state = ref({
    products: []
  })
  const products = ref([
    {
      id: 1,
      name: "Grape juice",
      description: "Grape juice from USA",
      price: 10,
      cardColor: "#805a98",
      isInState: false
    },
    {
      id: 2,
      name: "Apple juice",
      description: "Apple juice from China",
      price: 20,
      cardColor: "#ba4e4e",
      isInState: false
    },
    {
      id: 3,
      name: "Orange juice",
      description: "Orange juice from Japan",
      price: 30,
      cardColor: "#d68348",
      isInState: false
    }
  ])
  const isCartOpen = ref(true)
  provide("products", products)
  provide("state", state)

  const toggleCart = () => {
    isCartOpen.value = !isCartOpen.value
  }

  const addProductToCart = (productId) => {
    const product = products.value.find(p => p.id === productId)
    if(product){
      state.value.products.push(product)
      product.isInState = !product.isInState
    }
  }
  const removeProductFromCart = (productId) => {
    console.log("remove product from cart" + productId)
    const product = products.value.find(p => p.id === productId)
    if(product){
      state.value.products = state.value.products.filter(p => p.id !== productId)
      product.isInState = !product.isInState
    }
  }

</script>

<template>
  <div class="container">
    <div class="nav-bar">
      <p class="logo"><i class="pi pi-bullseye"></i>Juices shop</p>
      <button @click="toggleCart" class="my-cart-btn"><i class="pi pi-shopping-cart"></i></button>
    </div>
    <ProductsWrapper
        v-if="!isCartOpen"
        @remove-product-from-cart="removeProductFromCart"
        @add-product-to-cart="addProductToCart"
    />
    <CartSection
        v-else
        @go-to-homepage="isCartOpen = !isCartOpen"
        @remove-product-from-cart="removeProductFromCart"
    />
  </div>
</template>

<style scoped>
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .container .nav-bar {
    height: 4rem;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 1rem;
    background-color: var(--color-white);
  }
  .container .nav-bar .logo{
    font-size: 2rem;
    color: var(--color-text);
  }
  .container .nav-bar .logo i{
    margin-right: 0.5rem;
  }
  .container .nav-bar .my-cart-btn{
    height: 3.2rem;
    width: 3.2rem;
    border: none;
    background-color: var(--color-btn-1);
    border-radius: 50%;
    font-size: 1.3rem;
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--color-white);
    cursor: pointer;
  }
  .container .nav-bar .my-cart-btn:hover{
    background-color: var(--color-btn-1-hover);
  }
</style>
