<script setup>
const props = defineProps(["width", "height"])
</script>

<template>
  <button :style="{width: props.width || '100%', height: props.height || '2.5rem' }" class="default-button">
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
</style>