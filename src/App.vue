<script>
import axios from "axios";
export default {
  mounted() {
    axios.get("/api/wp-json/wc/store/products?page=1").then((response) => {
      console.log(response);
    });
  },
};
</script>

<template><h1>Greet App</h1></template>

<style scoped></style>
