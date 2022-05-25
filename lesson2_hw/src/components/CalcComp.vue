<template>
  <div>
    <div class="main">
      <div class="screen">
        <!--<input type="number" v-model.number="op1" />
        <input type="number" v-model.number="op2" />-->
        <input type="text" v-model="op1" />
        <input type="text" v-model="op2" />
        <div class="equ">=</div>
        <div class="res">{{ result }}</div>
      </div>
      <div class="error" v-show="error">
        {{ error }}
      </div>

      <div class="changeOperator">
        <input type="radio" id="one" value="op1" v-model="picked" />
        <label for="one">OP1</label>
        <input type="radio" id="two" value="op2" v-model="picked" />
        <label for="two">OP2</label>
      </div>

      <!--<div class="calc">
        <button @click="add">+</button>
        <button @click="sub">-</button>
        <button @click="mult">*</button>
        <button @click="div">/</button>
        <button @click="pow">x<sup>y</sup></button>
        <button @click="intDiv">DIV</button>
      </div>-->
      <div class="functionField">
        <div class="numberField">
          <button
            v-for="number of calcNumbers"
            :key="number"
            @click="addNumber(number)"
          >
            {{ number }}
          </button>
        </div>
        <div class="calc">
          <button
            v-for="operator in operators"
            :key="operator"
            @click="calculate(operator)"
          >
            {{ operator }}
          </button>
        </div>
      </div>
      <div class="clear">
        <button @click="reset">RESET</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CalcComp",
  data() {
    return {
      op1: "0",
      op2: "0",
      result: 0,
      picked: "op1",
      error: "",
      calcNumbers: [1, 2, 3, 4, 5, 6, 7, 8, 9, 0],
      operators: ["+", "-", "/", "*", "POW", "DIV"],
    };
  },
  methods: {
    calculate(operator) {
      this.error = "";
      // eslint-disable-next-line default-case
      switch (operator) {
        case "+":
          //console.log("!");
          this.add();
          break;
        case "-":
          this.sub();
          break;
        case "*":
          this.mult();
          break;
        case "/":
          this.div();
          break;
        case "POW":
          this.pow();
          break;
        case "DIV":
          this.intDiv();
          break;
      }
    },
    addNumber(number) {
      //console.log(number, picked);
      this[this.picked] += String(number);
    },
    add() {
      const { op1, op2 } = this;
      this.error = "";
      this.result = +op1 + +op2;
    },
    sub() {
      const { op1, op2 } = this;
      this.error = "";
      this.result = op1 - op2;
    },
    mult() {
      const { op1, op2 } = this;
      this.error = "";
      this.result = op1 * op2;
    },
    div() {
      const { op1, op2 } = this;
      this.error = "";
      if (this.op2 === 0 || this.op2 == "")
        return (this.error = "На ноль делить нельзя!");
      this.result = (op1 / op2).toFixed(2);
    },
    pow() {
      const { op1, op2 } = this;
      this.error = "";
      this.result = Math.pow(op1, op2);
    },
    intDiv() {
      const { op1, op2 } = this;
      this.error = "";
      if (this.op2 === 0) return (this.error = "На ноль делить нельзя!");
      this.result = Math.floor(op1 / op2);
    },
    reset() {
      this.error = "";
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
  height: 400px;
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
  .error {
    color: #f00;
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
      font-size: 13px;
      font-weight: bold;
    }
  }
  .clear {
    height: 40px;
  }
}
</style>
