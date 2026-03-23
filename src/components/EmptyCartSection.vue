<script setup>
import DefaultButton from "@/components/buttons/DefaultButton.vue";

defineEmits(['go-to-homepage']);
</script>

<template>
  <div class="empty-cart-section">
    <div class="row-1">
      <div class="icon">
        <i class="pi pi-cart-arrow-down"></i>
      </div>
        <div class="description">
          <p>Your cart is empty</p>
          <DefaultButton @click="$emit('go-to-homepage')">Go to homepage</DefaultButton>
        </div>
    </div>
  </div>
</template>

<style scoped>
  .empty-cart-section{
    width: 100%;
  }
  .empty-cart-section .row-1{
    display: flex;
  }
  .empty-cart-section .row-1 .icon{
    width: 20rem;
    height: 20rem;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 12rem;
    color: var(--color-text);
  }
  .empty-cart-section .row-1 .description{
    display: flex;
    flex-direction: column;
    justify-content: center;
    font-size: 2.2rem;
    color: var(--color-text);
    gap: 1rem
  }
</style>