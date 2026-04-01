<script setup>
import DefaultButton from "@/components/buttons/DefaultButton.vue";
import {computed, inject, reactive, ref, watch} from "vue";
const productsTotalPrice = inject("productsTotalPrice");

defineEmits(['payment-success'])

const tempExpDate = reactive({
  month: "",
  year: ""
})

const currentYear = new Date().getFullYear() % 100
const cardCredentials = ref({
  number: "",
  expDate: {
    month: undefined,
    year: undefined
  },
  cvc: "",
  name: ""
})

const errors = reactive({
  number: "",
  cvc: "",
  name: "",
  expDate: ""
})
const isFormValid = reactive({
  number: false,
  cvc: false,
  name: false,
  expMonth: false,
  expYear: false
})

const validateFormInput = (type) => {
  switch (type) {
    case "number": {
      let rawValue = cardCredentials.value.number.toString().replace(/\D/g, '')
      isFormValid.number = false
      if (rawValue.length === 0) {
        errors.number = "Please enter a card number"
        cardCredentials.value.number = ""
        break
      }
      if (rawValue.length < 16) {
        errors.number = "Card number is too short"
        cardCredentials.value.number = rawValue
        break
      }
      if (rawValue.length > 16) {
        cardCredentials.value.number = rawValue.slice(0, 16)
      }
      errors.number = ""
      isFormValid.number = true
      break
    }
    case "cvc": {
      let rawValue = cardCredentials.value.cvc.toString().replace(/\D/g, '')
      isFormValid.cvc = false
      if (rawValue.length === 0) {
        errors.cvc = "Please enter cvc"
        cardCredentials.value.cvc = ""
        break
      }
      if (rawValue.length < 3) {
        errors.cvc = "CVC is too short"
        cardCredentials.value.cvc = rawValue
        break
      }
      if (rawValue.length > 3) {
        cardCredentials.value.cvc = rawValue.slice(0, 3)
      }
      errors.cvc = ""
      isFormValid.cvc = true
      break
    }
    case "name": {
      let rawValue = cardCredentials.value.name.toString().replace(/[^a-zA-Z\s]/g, '').toUpperCase()
      isFormValid.name = false
      if (rawValue.length === 0) {
        errors.name = "Please enter Cardholder name"
        cardCredentials.value.name = ""
        break
      }

      if (rawValue.length > 26) {
        cardCredentials.value.name = rawValue.slice(0, 26)
        break
      }
      cardCredentials.value.name = rawValue
      errors.name = ""
      isFormValid.name = true
      break
    }
    case "expDate": {
      console.log(cardCredentials.value.expDate.month, cardCredentials.value.expDate.year)
      isFormValid.expMonth = false
      if (isFormValid.expMonth < 1 && isFormValid.expMonth > 12) {
        errors.expDate = "Invalid expiration month"
        break
      }
      if (isFormValid.expYear < currentYear && isFormValid.expYear > currentYear + 10) {
        errors.expDate = "Invalid expiration year"
        break
      }
      isFormValid.expMonth = true
      isFormValid.expYear = true
      errors.expDate = ""
      break
    }
  }
}
const isPaymentFormValid = computed(() => {
  return isFormValid.name && isFormValid.cvc && isFormValid.number && isFormValid.expMonth && isFormValid.expYear
})

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
                @input="validateFormInput('number')"
                type="text"
                v-model="cardCredentials.number"
                :class="{invalid: errors.number}"
            >
            <p class="credentials-error">{{ errors.number }}</p>
          </div>
          <div class="row-2">
            <div class="expiration-date">
              <label>Expiration date</label>
              <select @change="validateFormInput('expDate')" v-model="cardCredentials.expDate.month">
                <option :value=undefined disabled>MM</option>
                <option v-for="month in 12" :value="month">{{ month }}</option>
              </select>
              <slot>/</slot>
              <select @change="validateFormInput('expDate')" v-model="cardCredentials.expDate.year">
                <option :value=undefined disabled>YY</option>
                <option
                    v-for="n in 11"
                    :value="currentYear + (n - 1) + 2000">
                  {{ currentYear + (n - 1) }}
                </option>
              </select>
            </div>
            <div class="cvc">
              <label>CVC</label>
              <input
                  @input="validateFormInput('cvc')"
                  placeholder="999"
                  v-model.number.trim="cardCredentials.cvc"
                  :class="{invalid: errors.cvc}"
              >
            </div>
            <p class="credentials-error">{{ errors.cvc }}</p>
          </div>
          <div class="row-3">
            <label>Cardholder name</label>
            <input
                @input="validateFormInput('name')"
                type="text"
                placeholder="CARDHOLDER NAME"
                v-model="cardCredentials.name"
                :class="{invalid: errors.name}"
            >
            <p class="credentials-error">{{ errors.name }}</p>
          </div>
        </div>
      </div>
      <DefaultButton :disabled="!isPaymentFormValid" :width="'80%'" :height="'3rem'">Pay {{ productsTotalPrice }}$</DefaultButton>
    </form>
  </div>
</template>

<style scoped>
.payment-section {
  width: 70%;
  padding: 1rem;
}

.payment-section .header {
  font-size: 1.4rem;
}

.payment-section .payment-form {
  margin-top: 1rem;
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.payment-section .payment-form input {
  height: 2.5rem;
  border-radius: 0.5rem;
  padding: 1rem;
}

.payment-section .payment-form input.invalid {
  border: 1.5px solid red
}

.payment-section .payment-form select {
  height: 2.5rem;
  border-radius: 0.5rem;
  padding: 0 1rem 0 1rem;
  border: none;
}
.payment-section .payment-form .credentials-error {
  color: var(--color-pale-red);
}
.payment-section .payment-form .card {
  height: 30rem;
  width: 80%;
  border-radius: 1rem;
  background-color: var(--color-pale-green);
  box-shadow: var(--box-shadow);
  padding: 2rem;

}

.payment-section .payment-form .card .header-row {
  font-size: 1.8rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 5rem;
}

.payment-section .payment-form .card .info-row {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.payment-section .payment-form .card .info-row .row-1 {
  display: flex;
  flex-direction: column;
  gap: 0.5rem
}

.payment-section .payment-form .card .info-row .row-2 {
  display: flex;
  justify-content: end;
  gap: 1rem;
}

.payment-section .payment-form .card .info-row .row-2 .expiration-date {
  display: flex;
  align-items: center;
  gap: 0.5rem
}

.payment-section .payment-form .card .info-row .row-2 .expiration-date input {
  width: 5rem;
}

.payment-section .payment-form .card .info-row .row-2 .cvc {
  display: flex;
  align-items: center;
  gap: 0.5rem;

}

.payment-section .payment-form .card .info-row .row-2 .cvc input {
  width: 5rem;
}

.payment-section .payment-form .card .info-row .row-3 {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

</style>