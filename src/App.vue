<script>
import CardGrid from "./components/Layout/CardGrid/CardGrid.vue";
export default {
  components: { CardGrid },
  provide() {
    return {
      onOrder: this.orderData,
    };
  },
  data() {
    return {
      greetData: [],
      page: 1,
      isLoading: false,
    };
  },

  methods: {
    orderData(value) {
      const newData = [...this.greetData];
      this.greetData = newData.sort((personOne, personTwo) => {
        if (!personOne[value] || !personTwo[value]) {
          return;
        }
        let comparisonResult;

        if (value === "name") {
          comparisonResult = personOne[value].localeCompare(
            personTwo[value],
            "en",
            { sensitivity: "base" }
          );
        } else if (value === "price") {
          const priceOne = personOne[value] || 0;
          const priceTwo = personTwo[value] || 0;
          comparisonResult = priceOne - priceTwo;
        }

        if (comparisonResult < 0) {
          return -1;
        }
        if (comparisonResult > 0) {
          return 1;
        }
        return 0;
      });
    },
    handleScroll() {
      const element = this.$refs.pageRef;

      if (
        !this.isLoading &&
        element.getBoundingClientRect().bottom - 1000 < window.innerHeight
      ) {
        this.page++;
        this.setGreetData();
      }
    },
    setGreetData() {
      this.isLoading = true;
      fetch(`/api/wp-json/wc/store/products?page=${this.page}`)
        .then((response) => {
          return response.json();
        })
        .then((result) => {
          this.greetData = [...this.greetData, ...result].map((person) => {
            return {
              ...person,
              price: +person.prices.price,
            };
          });
          this.isLoading = false;
        });
    },
  },
  mounted() {
    this.setGreetData();
    window.addEventListener("scroll", this.handleScroll);
  },
  unmounted() {
    window.removeEventListener("scroll", this.handleScroll);
  },
};
</script>

<template>
  <main>
    <h1>Greet App</h1>
    <div ref="pageRef" class="container">
      <card-grid v-if="greetData.length > 0" :cardData="greetData"></card-grid>
      <h1 v-if="isLoading">Loading...</h1>
    </div>
  </main>
</template>

<style></style>
