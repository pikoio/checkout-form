<script setup>
defineEmits(['toggle-cart'])
</script>

<template>
  <div class="nav-bar">
    <p class="logo"><i class="pi pi-bullseye"></i>Juices shop</p>
    <button @click="$emit('toggle-cart')" class="my-cart-btn"><i class="pi pi-shopping-cart"></i></button>
  </div>
</template>

<style scoped>
.nav-bar {
  height: 4rem;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1rem;
  background-color: transparent;
}

.nav-bar .logo {
  font-size: 2rem;
  color: var(--color-text);
}

.nav-bar .logo i {
  margin-right: 0.5rem;
}

.nav-bar .my-cart-btn {
  height: 3.2rem;
  width: 3.2rem;
  border: none;
  background-color: var(--color-btn-1);
  border-radius: 50%;
  font-size: 1.3rem;
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--color-white);
  cursor: pointer;
}

.nav-bar .my-cart-btn:hover {
  background-color: var(--color-btn-1-hover);
}
</style>