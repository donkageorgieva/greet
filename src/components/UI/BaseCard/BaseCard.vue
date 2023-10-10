<script>
import BaseButton from "../BaseButton/BaseButton.vue";

export default {
  components: { BaseButton },
  props: {
    imgSrc: String,
    name: String,
    description: String,
    category: Array,
    price: Number,
  },
  methods: {
    onAddToCart() {
      window.location.href = `https://greet.bg/?add-to-
cart=5589.`;
    },
  },
  computed: {
    formatCategory() {
      let reformatedCategories = [];
      for (const oneCategory in this.category) {
        reformatedCategories.push(this.category[oneCategory].name);
      }
      return reformatedCategories.join(" ");
    },
    formattedPrice() {
      return this.price + "BGN";
    },
  },
};
</script>

<template>
  <article class="card">
    <img :src="imgSrc" class="card__img" />
    <div class="card__body">
      <h2 v-html="name"></h2>
      <h4>{{ formatCategory }}</h4>
      <span v-html="description"></span>
      <p>{{ formattedPrice }}</p>
    </div>
    <div class="card__footer">
      <base-button @onClick="onAddToCart">Add to Cart</base-button>
    </div>
  </article>
</template>

<style scoped>
.card {
  max-width: 20%;
  background-color: white;
  border-radius: 1rem;
  box-shadow: 0 20px 40px -14px rgba(0, 0, 0, 0.25);
  display: flex;
  align-items: space-between;
  flex-direction: column;
  overflow: hidden;
  margin: 2rem;
  height: 100%;
  height: 40rem;
}
.card__body {
  padding: 0rem 2rem 0rem;
  max-height: 30rem;
  overflow-x: hidden;
  overflow-y: scroll;
}
.card__img {
  height: 20rem;
  object-fit: cover;
  object-position: 100% 20%;

  vertical-align: middle;
}
.card__footer {
  padding: 1rem;
  text-align: center;
  position: relative; /* Make the footer relative to its parent .card */
  margin-top: auto;
}
@media (min-width: 40rem) {
  .card {
    width: 50%;
  }
}

@media (min-width: 56rem) {
  .card {
    width: 30%;
  }
}
</style>
