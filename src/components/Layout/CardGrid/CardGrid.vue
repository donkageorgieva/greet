<script>
import BaseCard from "../../UI/BaseCard/BaseCard.vue";
import Dropdown from "../../UI/Dropdown/Dropdown.vue";
export default {
  components: { BaseCard, Dropdown },
  methods: {
    onChangeOrder() {},
  },
  props: {
    cardData: Array,
  },
};
</script>

<template>
  <dropdown
    :name="'order'"
    :label="'Order By'"
    :options="['name', 'price']"
    @change="onChangeOrder"
  ></dropdown>
  <section class="container">
    <base-card
      v-for="data in cardData"
      :key="data.id"
      :imgSrc="data.images[0].src"
      :name="data.name"
      :description="data['short_description']"
      :category="data.categories"
      :price="data.price"
    />
  </section>
</template>

<style scoped>
section {
  display: flex;
  flex-wrap: wrap;
}
</style>
