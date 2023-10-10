<script>
export default {};
</script>

<template>
  <button @click="$emit('onClick')"><slot></slot></button>
</template>
