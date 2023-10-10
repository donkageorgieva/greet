<script>
export default {};
</script>

<template>
  <button @click="$emit('onClick')" :class="$style.button">
    <slot></slot>
  </button>
</template>

<style module>
.button {
  background: rgb(66, 133, 244);
  border: none;
  border-radius: 8px;
  color: white;
  padding: 0.5rem 1rem;
  font-size: 18px;
}
</style>
