<script setup>
import {reactive} from "vue";

const props = defineProps({
  width: { type: String, default: '100%' },
  height: { type: String, default: '2.5rem' },
  disabled: { type: Boolean, default: false }
})
</script>

<template>
  <button
      class="default-button"
      :class="{disabled: props.disabled}"
      :style="{ width: props.width, height: props.height }"
      :disabled="props.disabled">
    <slot/>
  </button>
</template>

<style scoped>
  .default-button{
    background-color: var(--color-btn-1);
    border-radius: 0.2rem;
    color: var(--color-white);
    font-size: 1rem;
  }
  .default-button:hover{
    background-color: var(--color-btn-1-hover);
  }
  .default-button.disabled{
    background-color: var(--color-dark-grey);
    cursor: not-allowed;
  }
</style>