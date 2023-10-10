<script>
export default {
  props: {
    options: Array,
    name: String,
  },
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
    <select :name="name" :id="name" @change="onChange" v-model="selectedOption">
      <option v-for="option in options" :key="option" :value="option">
        {{ option }}
      </option>
    </select>
  </div>
</template>

<style scoped></style>
