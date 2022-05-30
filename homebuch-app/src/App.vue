<template>
  <div id="app">
    <header>
      <h1>My Homebuch</h1>
    </header>
    <main>
      <div>
        <AddCostForm @AddCost='addNewPayment' />
        <CostList :items="paymentsList" />
      </div>
    </main>
  </div>
</template>

<script>
import CostList from "./components/CostList.vue";
import AddCostForm from "./components/AddCostForm.vue";

export default {
  name: "App",
  data() {
    return {
      paymentsList: [],
    };
  },
  methods: {
    fetchData() {
      return [
        {
          date: "27.05.2022",
          category: "Food",
          value: 847,
        },
        {
          date: "28.05.2022",
          category: "Transport",
          value: 449,
        },
        {
          date: "29.05.2022",
          category: "Medical",
          value: 554,
        },
      ];
    },
    addNewPayment(data) {
      console.log(data);
      this.paymentsList.push(data);
    },
  },
  components: {
    CostList,
    AddCostForm,
  },

  created() {
    this.paymentsList = this.fetchData();
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  margin-left: 50px;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
