<script setup>
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
    <button @click="$emit('go-to-homepage')" class="home-page-btn">Go to Homepage</button>
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
    color: #56aa54;
  }
  .success-payment-section .success-header{
    color: #557c4e;
    font-size: 2rem;
  }
  .success-payment-section .success-description{
    font-size: 1.1rem;
    color: #557c4e;
  }
  .success-payment-section .payment-info{
    display: flex;
    flex-direction: column;
    align-items: center;
    color: #56aa54;
  }
  .success-payment-section .payment-info .row{
    display: flex;
    width: 20rem;
    justify-content: space-between;
  }
  .success-payment-section .home-page-btn{
    border: none;
    width: 20rem;
    height: 2rem;
    background-color: #56aa54;
    color: #ffffff;
    border-radius: 0.2rem;
  }


</style>