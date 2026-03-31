<script setup>
import {ref} from "vue";

const props = defineProps(["product"])
const emit = defineEmits(["remove-product-from-cart"])

const productItemStyle = ref('open')

const deleteProductFromCart = () => {
  productItemStyle.value = 'close'
  setTimeout(() => {
    emit("remove-product-from-cart", props.product.id)
  }, 1000)
}

</script>

<template>
  <div  class="product-item" :class="productItemStyle">
    <div class="icon">
      <i :class="product.icon"></i>
    </div>
    <div class="info">
      <div class="row-1">
        <p>{{ product.name }}</p>
        <div
            @click="deleteProductFromCart"
            class="delete-btn">
          <i class="pi pi-trash"></i>
        </div>
      </div>
      <div class="row-2">
        <p>{{ product.price }}$</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
  .product-item{
    height: 6rem;
    padding: 1rem;
    background-color: var(--color-pale-green);
    color: var(--color-text);
    display: flex;
    border-radius: 1rem;
    box-shadow: var(--box-shadow);
    width: 100%;
    transition: 1s;
  }

  .product-item.close{
    width: 10%;
  }
  .product-item.close .icon{
    display: none
  }
  .product-item.close .info{
    display: none
  }

  .product-item .icon{
    width: 4rem;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 2rem;
  }
  .product-item .info{
    display: flex;
    flex-direction: column;
    flex: 1;
  }
  .product-item .info .row-1{
    height: 50%;
    font-size: 1rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .product-item .info .row-1 .delete-btn{
    width: 1.5rem;
    height: 1.5rem;
    background-color: var(--color-btn-1);
    border-radius: 0.2rem;
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--color-white);
    font-size: 0.9rem;
    cursor: pointer;
  }
  .product-item .info .row-1 .delete-btn:hover{
    background-color: var(--color-btn-1-hover);
  }
  .product-item .info .row-2{
    height: 50%;
    display: flex;
    align-items: center;
    font-size: 1.2rem;
  }


</style>