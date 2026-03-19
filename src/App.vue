<script setup>
  import ProductsWrapper from "@/components/ProductsWrapper.vue";
  import {provide, ref} from "vue";
  import CartSection from "@/components/CartSection.vue";
  const state = ref({
    products: [
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
    ]
  })
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
  const isCartOpen = ref(true)
  provide("products", products)
  provide("state", state)

  const toggleCart = () => {
    isCartOpen.value = !isCartOpen.value
  }

</script>

<template>
  <div class="container">
    <div class="nav-bar">
      <p class="logo"><i class="pi pi-bullseye"></i>Juices shop</p>
      <button @click="toggleCart" class="my-cart-btn"><i class="pi pi-shopping-cart"></i></button>
    </div>
    <ProductsWrapper v-if="!isCartOpen"/>
    <CartSection v-else @go-to-homepage="isCartOpen = !isCartOpen"/>

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
    background-color: #ffffff;
  }
  .container .nav-bar .logo{
    font-size: 2rem;
    color: #557c4e;
  }
  .container .nav-bar .logo i{
    margin-right: 0.5rem;
  }
  .container .nav-bar .my-cart-btn{
    height: 3.2rem;
    width: 3.2rem;
    border: none;
    background-color: #55a953;
    border-radius: 50%;
    font-size: 1.3rem;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    cursor: pointer;
  }
  .container .nav-bar .my-cart-btn:hover{
    background-color: #3e9a3d;
  }
</style>
