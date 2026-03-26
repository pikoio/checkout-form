<script setup>
import DefaultButton from "@/components/buttons/DefaultButton.vue";
import {computed, ref, watch} from "vue";

defineEmits(['payment-success'])

const cardCredentials = ref({
  number: "",
  expDate: "",
  cvc: undefined,
  name: ""
})

const currentYear = new Date().getFullYear() % 100

const tempExpDate = ref({
  month: "",
  year: ""
})

const validateCardNumber = computed(() => {

})
// Number
watch(
    () => cardCredentials.value.number,
    (newNumber, oldNumber) => {
      let rawNumber  = newNumber.toString().replace(/\D/g, '')
      cardCredentials.value.number = newNumber.toString().length > 19 ? oldNumber : rawNumber
    }
)
// CVC
watch(
    () => cardCredentials.value.cvc,
    (newCVC, oldCVC) => {
      cardCredentials.value.cvc = newCVC.toString().length > 3 ? oldCVC : newCVC
    }
)
// Cardholder name
watch(
    () => cardCredentials.value.name,
    (newCardholderName, oldCardholderName) => {
      let rawCardHolderName = newCardholderName.toString().replace(/[^a-zA-Z\s]/g, '')
      cardCredentials.value.name = newCardholderName.toString().length > 20 ? oldCardholderName : rawCardHolderName
      cardCredentials.value.name = cardCredentials.value.name.toString().toUpperCase()
    }
)

</script>

<template>
  <div class="payment-section">
    <p class="header">Payment</p>
    <form class="payment-form">
      <div class="card">
        <div class="header-row">
          <i class="pi pi-check-circle"></i>
          <p>Credit card</p>
        </div>
        <div class="info-row">
          <div class="row-1">
            <label>Card number</label>
            <input
                type="text"
                v-model="cardCredentials.number"
            >
          </div>
          <div class="row-2">
            <div class="expiration-date">
              <label>Expiration date</label>
              <select v-model="tempExpDate.month">
                <option value="" disabled>MM</option>
                <option v-for="month in 12" :value="month">{{ month }}</option>
              </select>
              <slot>/</slot>
              <select v-model="tempExpDate.year">
                <option value="" disabled>YY</option>
                <option
                    v-for="n in 11"
                    :value="currentYear + (n - 1)">
                  {{ currentYear + (n - 1) }}
                </option>
              </select>
            </div>
            <div class="cvc">
              <label>CVC</label>
              <input
                  type="number"
                  placeholder="999"
                  v-model.number.trim="cardCredentials.cvc"
              >
            </div>
          </div>
          <div class="row-3">
            <label>Cardholder name</label>
            <input
                type="text"
                placeholder="CARDHOLDER NAME"
                v-model="cardCredentials.name"
            >
          </div>
        </div>
      </div>
      <DefaultButton :width="'80%'" :height="'3rem'">Pay 500$</DefaultButton>
    </form>
  </div>
</template>

<style scoped>
  .payment-section {
    width: 70%;
    padding: 1rem;
  }
  .payment-section .header{
    font-size: 1.4rem;
  }
  .payment-section .payment-form{
    margin-top: 1rem;
    display: flex;
    flex-direction: column;
    gap: 2rem;
  }
  .payment-section .payment-form input{
    height: 2.5rem;
    border-radius: 0.5rem;
    padding: 1rem;
  }
  .payment-section .payment-form select{
    height: 2.5rem;
    border-radius: 0.5rem;
    padding: 0 1rem 0 1rem;
    border: none;
  }

  .payment-section .payment-form .card{
    height: 30rem;
    width: 80%;
    border-radius: 1rem;
    background-color: var(--color-pale-green);
    box-shadow: var(--box-shadow);
    padding: 2rem;

  }
  .payment-section .payment-form .card .header-row{
    font-size: 1.8rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 5rem;
  }
  .payment-section .payment-form .card .info-row{
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
  }
  .payment-section .payment-form .card .info-row .row-1{
    display: flex;
    flex-direction: column;
    gap: 0.5rem
  }
  .payment-section .payment-form .card .info-row .row-2{
    display: flex;
    justify-content: end;
    gap: 1rem;
  }
  .payment-section .payment-form .card .info-row .row-2 .expiration-date{
    display: flex;
    align-items: center;
    gap: 0.5rem
  }
  .payment-section .payment-form .card .info-row .row-2 .expiration-date input{
    width: 5rem;
  }
  .payment-section .payment-form .card .info-row .row-2 .cvc{
    display: flex;
    align-items: center;
    gap: 0.5rem;

  }
  .payment-section .payment-form .card .info-row .row-2 .cvc input{
    width: 5rem;
  }
  .payment-section .payment-form .card .info-row .row-3{
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }

</style>