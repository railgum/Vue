<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <Calc />
  </div>
</template>

<script>
import Calc from "./components/Calc.vue";

export default {
  name: "App",
  data() {
    return {
      msg: "Hello Rail",
      counter: 0,
    };
  },
  methods: {
    inc(step, event) {
      console.log(event);
      this.counter += step;
    },
  },
  components: {
    Calc,
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
