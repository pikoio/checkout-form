<script setup>
import ProductsWrapper from "@/components/ProductsWrapper.vue";
import {provide, ref} from "vue";
import CartSection from "@/components/CartSection.vue";
import NavBar from "@/components/NavBar.vue";

const state = ref({
  products: [
    {
      id: 1,
      name: "Grape juice",
      description: "Grape juice from USA",
      price: 10,
      cardColor: "#805a98",
      isInState: false,
      icon: "pi pi-sun"

    },
    {
      id: 2,
      name: "Apple juice",
      description: "Apple juice from China",
      price: 20,
      cardColor: "#ba4e4e",
      isInState: false,
      icon: "pi pi-apple"
    },
    {
      id: 3,
      name: "Orange juice",
      description: "Orange juice from Japan",
      price: 30,
      cardColor: "#d68348",
      isInState: false,
      icon: "pi pi-sparkles"
    }
  ]
})
const products = ref([
  {
    id: 1,
    name: "Grape juice",
    description: "Grape juice from USA",
    price: 10,
    cardColor: "#805a98",
    isInState: false,
    icon: "pi pi-sun"

  },
  {
    id: 2,
    name: "Apple juice",
    description: "Apple juice from China",
    price: 20,
    cardColor: "#ba4e4e",
    isInState: false,
    icon: "pi pi-apple"
  },
  {
    id: 3,
    name: "Orange juice",
    description: "Orange juice from Japan",
    price: 30,
    cardColor: "#d68348",
    isInState: false,
    icon: "pi pi-sparkles"
  }
])
const isCartOpen = ref(true)
provide("products", products)
provide("state", state)

const toggleCart = () => {
  isCartOpen.value = !isCartOpen.value
}

const buyNowProduct = (productId) => {
  toggleCart()
  addProductToCart(productId)
}

const addProductToCart = (productId) => {
  const product = products.value.find(p => p.id === productId)
  if (product) {
    state.value.products.push(product)
    product.isInState = !product.isInState
  }
}
const removeProductFromCart = (productId) => {
  console.log("remove product from cart" + productId)
  const product = products.value.find(p => p.id === productId)
  if (product) {
    state.value.products = state.value.products.filter(p => p.id !== productId)
    product.isInState = !product.isInState
  }
}

</script>

<template>
  <div class="container">
    <NavBar @toggle-cart="toggleCart"/>
    <ProductsWrapper
        v-if="!isCartOpen"
        @remove-product-from-cart="removeProductFromCart"
        @add-product-to-cart="addProductToCart"
        @buy-now-product="buyNowProduct"
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

</style>
