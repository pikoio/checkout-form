<script setup>
import DefaultButton from "@/components/buttons/DefaultButton.vue";

defineEmits(['payment-success'])
</script>

<template>
  <div class="payment-section">
    <p class="header">Payment</p>
    <form class="payment-form">
      <div class="form-card">
        <div class="row-1">
          <p class="bank-title">Credit card</p>
          <i class="pi pi-exclamation-circle error-indicator" ></i>
          <i class="pi pi-check-circle aproved-indicator"></i>
          <i class="pi pi-bullseye"></i>
        </div>
        <div class="row-2">
          <label class="form-label">Card number</label>
          <input class="form-input" type="number">
        </div>
        <div class="row-3">
          <label class="form-label">Expiration date</label>
          <input class="form-input" type="number">
            <div class="divide">
              <p>/</p>
            </div>
          <input class="form-input" type="number">
        </div>
        <div class="row-4">
          <label class="form-label">Name on card</label>
          <input class="form-input" type="text">
        </div>
      </div>
      <DefaultButton @click="$emit('payment-success')" class="confirm-payment-btn">Confirm payment</DefaultButton>
    </form>
  </div>
</template>

<style scoped>
  .payment-section {
    width: 65%;
    padding: 1rem;
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }
  .payment-section .header{
    font-size: 1.4rem;
    color: var(--color-text);
  }
  .payment-section .payment-form{
    display: flex;
    flex-direction: column;
    border-radius: 1rem;
    background-color: #e6f2e6;
    padding: 2rem;
  }
  .payment-section .payment-form .form-card .form-label{
    font-size: 0.8rem;
    color: var(--color-text);
    margin-bottom: 0.2rem;
  }
  .payment-section .payment-form .form-card .form-input{
    height: 2.5rem;
    border: none;
    border-radius: 0.2rem;
  }
  .payment-section .payment-form .form-card .row-1{
    display: flex;
    align-items: center;
    justify-content: space-between;
    color: var(--color-text);
    margin-bottom: 1.5rem;
  }
  .payment-section .payment-form .form-card .row-1 .error-indicator{
    color: var(--color-pale-red);
  }
  .payment-section .payment-form .form-card .row-1 .bank-title{
    font-size: 1.4rem;
  }
  .payment-section .payment-form .form-card .row-1 i{
    font-size: 1.5rem;
  }
  .payment-section .payment-form .form-card .row-2{
    display: flex;
    flex-direction: column;
    margin-bottom: 1rem;
  }
  .payment-section .payment-form .form-card .row-3{
    width: 80%;
    display: flex;
    align-items: center;
    justify-content: end;
    height: 2.5rem;
  }
  .payment-section .payment-form .form-card .row-3 .form-label{
    margin-right: 0.5rem;
  }
  .payment-section .payment-form .form-card .row-3 .divide{
    font-size: 1.3rem;
    color: var(--color-text);
    background-color: var(--color-white);
    height: 100%;
    display: flex;
    align-items: center;
  }
  .payment-section .payment-form .form-card .row-3 .form-input{
    width: 4rem;
  }
  .payment-section .payment-form .form-card .row-4{
    margin-top: 1rem;
    display: flex;
    flex-direction: column;
  }

</style>