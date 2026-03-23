<script setup>
  import DefaultButton from "@/components/buttons/DefaultButton.vue";

  defineEmits(['go-to-homepage'])
</script>

<template>
  <div class="success-payment-section">
    <i class="pi pi-check-circle success-icon"></i>
    <p class="success-header">Payment successful</p>
    <p class="success-description">Your payment has been processed successfully.</p>
    <div class="payment-info">
      <div class="row">
        <p>Amount</p>
        <p>145$</p>
      </div>
      <div class="row">
        <p>Transaction ID</p>
        <p>TXN-38373878</p>
      </div>
      <div class="row">
        <p>Date</p>
        <p>Dec 15, 2026</p>
      </div>
    </div>
    <DefaultButton @click="$emit('go-to-homepage')">Go to Homepage</DefaultButton>
  </div>
</template>

<style scoped>
  .success-payment-section {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 1rem
  }
  .success-payment-section .success-icon{
    font-size: 10rem;
    color: var(--color-btn-1);
  }
  .success-payment-section .success-header{
    color: var(--color-text);
    font-size: 2rem;
  }
  .success-payment-section .success-description{
    font-size: 1.1rem;
    color: var(--color-text);
  }
  .success-payment-section .payment-info{
    display: flex;
    flex-direction: column;
    align-items: center;
    color: var(--color-text);
  }
  .success-payment-section .payment-info .row{
    display: flex;
    width: 20rem;
    justify-content: space-between;
  }
</style>