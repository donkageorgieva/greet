<script>
export default {
  props: {
    options: Array,
    name: String,
    label: String,
  },
  inject: ["onOrder"],
  data() {
    return {
      selectedOption: "",
    };
  },
  methods: {
    onChange() {
      this.$emit("onSelectItem", this.selectedOption);
    },
  },
};
</script>

<template>
  <div class="select">
    <label>{{ label }}</label>
    <select
      :name="name"
      :id="name"
      @change="onOrder(selectedOption)"
      v-model="selectedOption"
    >
      <option v-for="option in options" :key="option" :value="option">
        {{ option }}
      </option>
    </select>
  </div>
</template>

<style scoped></style>
