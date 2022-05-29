<template>
  <div id="app">
    <header>
      <div>My Homebuch</div>
    </header>
    <main>
      <div>
        <ExpenseList :items="paymentsList" />
      </div>
    </main>
  </div>
</template>

<script>
import ExpenseList from "./components/ExpenseList.vue";

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
          date: "10.05.2022",
          category: "Food",
          value: 358,
        },
        {
          date: "12.05.2022",
          category: "Transport",
          value: 2493,
        },
        {
          date: "15.05.2022",
          category: "Home",
          value: 774,
        },
      ];
    },
  },
  components: {
    ExpenseList,
  },
  created() {
    this.paymentsList = this.fetchData();
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
