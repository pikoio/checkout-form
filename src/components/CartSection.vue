<script setup>

import ProductsList from "@/components/ProductsList.vue";
import PaymentSection from "@/components/PaymentSection.vue";
import {ref} from "vue";
import SuccessPaymentSection from "@/components/SuccessPaymentSection.vue";

defineEmits("go-to-homepage")

const isFormValid = ref(true)

</script>

<template>
  <div class="cart-section">
    <template v-if="!isFormValid">
      <PaymentSection @payment-success="isFormValid = !isFormValid"/>
      <ProductsList/>
    </template>
    <SuccessPaymentSection v-else @go-to-homepage="$emit('go-to-homepage')"/>
  </div>
</template>

<style scoped>
  .cart-section {
    width: 100%;
    display: flex;
    justify-content: space-between;
  }
</style>