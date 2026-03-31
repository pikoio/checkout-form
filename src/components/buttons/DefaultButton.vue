<script setup>
const props = defineProps({
  width: { type: String, default: '100%' },
  height: { type: String, default: '2.5rem' },
})
</script>

<template>
  <button :style="{width: props.width, height: props.height }" class="default-button">
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