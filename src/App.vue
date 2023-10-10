<script>
// import axios from "axios";
import BaseCard from "./components/UI/BaseCard/BaseCard.vue";
export default {
  components: { BaseCard },
  mounted() {
    // axios.get("/api/wp-json/wc/store/products?page=1").then((response) => {
    //   console.log(response);
    // });
  },
};
</script>

<template>
  <h1>Greet App</h1>
  <base-card
    :imgSrc="'https://greet.bg/wp-content/uploads/2022/04/0631479001644578128_big.jpg'"
    :category="'Инфлуенсъри'"
    :name="'Виктор Стоянов &#8211; Ергенът'"
    :description="'<p>Участник в риалити шоуто &#8220;Ергенът&#8221;, Виктор е истински джентълмен. Заяви видео, записано лично от него, за да зарадваш свои близки с неповторима емоция.</p>'"
  ></base-card>
</template>

<style></style>
