<template>
  <div class="add">
    <div class="addButton">
      <button @click="toggle = !toggle">ADD NEW COST +</button>
    </div>
    <div
      class="addCost"
      v-show="toggle"
    >
      <input
        class="inputItem"
        type="text"
        placeholder="Date"
        v-model="date"
      >

      <input
        class="inputItem"
        type="text"
        placeholder="Category"
        v-model="category"
      >
      <input
        class="inputItem"
        type="text"
        placeholder="Value"
        v-model="value"
      >
      <button
        class="addCostButton"
        @click="addCost"
      >Add</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "AddCostForm",
  data() {
    return {
      value: "",
      category: "",
      date: "",
      toggle: false,
    };
  },
  computed: {
    paymentDate() {
      const currentDate = new Date();
      const day = currentDate.getDate();
      const month = currentDate.getMonth() + 1;
      const year = currentDate.getFullYear();
      return `${day}.${month}.${year}`;
    },
  },
  methods: {
    addCost() {
      const data = {
        value: +this.value,
        category: this.category,
        date: this.date || this.paymentDate,
      };
      this.$emit("AddCost", data);
      
    },
  },
};
</script>

<style lang="scss" scoped>
.add {
  width: 45%;
  .addButton {
    button {
      height: 50px;
      width: 250px;
      background-color: #43d373;
    }
  }
  .addCost {
    display: flex;
    flex-direction: column;
    margin-top: 15px;
    .inputItem {
      margin-top: 10px;
      width: 150px;
    }
    .addCostButton {
      display: inline-block;
      margin-top: 10px;
      width: 160px;
      background-color: #43d373;
    }
  }
}
</style>