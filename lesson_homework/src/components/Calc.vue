<template>
  <div>
    <div class="main">
      <div class="screen">
        <input type="number" v-model.number="op1" />
        <input type="number" v-model.number="op2" />
        <div class="equ">=</div>
        <div class="res">{{ result }}</div>
      </div>
      <div class="calc">
        <button @click="add">+</button>
        <button @click="sub">-</button>
        <button @click="mult">*</button>
        <button @click="div">/</button>
        <button @click="pow">x<sup>y</sup></button>
        <button @click="intDiv">DIV</button>
      </div>
      <div class="clear">
        <button @click="reset">RESET</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Calc",
  data() {
    return {
      op1: 0,
      op2: 0,
      result: 0,
    };
  },
  methods: {
    add() {
      this.result = this.op1 + this.op2;
    },
    sub() {
      this.result = this.op1 - this.op2;
    },
    mult() {
      this.result = this.op1 * this.op2;
    },
    div() {
      this.result = (this.op1 / this.op2).toFixed(2);
    },
    pow() {
      this.result = Math.pow(this.op1, this.op2);
    },
    intDiv() {
      this.result = Math.floor(this.op1 / this.op2);
    },
    reset() {
      this.result = 0;
      this.op1 = 0;
      this.op2 = 0;
    },
  },
};
</script>

<style scoped lang="scss">
.main {
  border: 2px solid black;
  display: flex;
  flex-direction: column;
  margin: 50px auto;
  width: 400px;
  height: 300px;
  .screen {
    margin: 20px auto;
    display: flex;
    justify-content: center;
    width: 300px;
    input {
      text-align: center;
      margin: 15px;
      width: 50px;
      height: 30px;
    }
    .equ {
      margin-top: 20px;
      margin-right: 15px;
      width: 20px;
      height: 20px;
    }
    .res {
      margin-top: 15px;
      text-align: center;
      padding-top: 5px;
      width: 60px;
      height: 30px;
      border: 1px solid black;
    }
  }
  .calc {
    margin: 30px auto;
    width: 200px;
    display: flex;
    flex-wrap: wrap;
    button {
      display: block;
      width: 50px;
      height: 35px;
      margin: 5px;
    }
  }
  .clear {
    height: 40px;
  }
}
</style>
