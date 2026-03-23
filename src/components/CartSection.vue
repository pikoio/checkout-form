<script setup>

import ProductsList from "@/components/ProductsList.vue";
import PaymentSection from "@/components/PaymentSection.vue";
import {inject, ref} from "vue";
import SuccessPaymentSection from "@/components/SuccessPaymentSection.vue";
import EmptyCartSection from "@/components/EmptyCartSection.vue";

defineEmits("go-to-homepage", "remove-product-from-cart");

const state = inject("state")

const isFormValid = ref(false)

</script>

<template>
  <div class="cart-section">
    <template v-if="state.products.length > 0">
      <template v-if="!isFormValid">
        <PaymentSection @payment-success="isFormValid = !isFormValid"/>
        <ProductsList @remove-product-from-cart="$emit('remove-product-from-cart', $event)"/>
      </template>
      <SuccessPaymentSection v-else @go-to-homepage="$emit('go-to-homepage')"/>
    </template>
    <EmptyCartSection v-else @go-to-homepage="$emit('go-to-homepage')"/>
  </div>
</template>

<style scoped>
  .cart-section {
    width: 100%;
    display: flex;
    justify-content: space-between;
  }
</style>