<script setup>

</script>

<template>
  <button class="default-button">
    <slot/>
  </button>
</template>

<style scoped>
  .default-button{
    background-color: var(--color-btn-1);
    height: 2.5rem;
    border-radius: 0.2rem;
    color: var(--color-white);
    font-size: 1rem;
  }
  .default-button:hover{
    background-color: var(--color-btn-1-hover);
  }
</style>