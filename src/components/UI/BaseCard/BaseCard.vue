<script>
export default {
  props: {
    imgSrc: String,
    name: String,
    description: String,
    category: String,
  },
};
</script>

<template>
  <article>
    <img :src="imgSrc" />
    <h2>{{ name }}</h2>
    <h4>{{ category }}</h4>
    <span v-html="description"></span>

    <button>Add to Cart</button>
  </article>
</template>

<style scoped></style>
