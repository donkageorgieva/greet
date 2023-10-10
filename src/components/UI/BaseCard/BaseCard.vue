<script>
import BaseButton from "../BaseButton/BaseButton.vue";

export default {
  components: { BaseButton },
  props: {
    imgSrc: String,
    name: String,
    description: String,
    category: String,
  },
  methods: {
    onAddToCart() {
      window.location.href = `https://greet.bg/?add-to-
cart=5589.`;
    },
  },
};
</script>

<template>
  <article>
    <img :src="imgSrc" />
    <h2>{{ name }}</h2>
    <h4>{{ category }}</h4>
    <span v-html="description"></span>

    <base-button @onClick="onAddToCart">My text</base-button>
  </article>
</template>

<style scoped></style>
