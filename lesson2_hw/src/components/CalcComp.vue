<template>
  <div>
    <div class="main">
      <div class="screen">
        <!--<input type="number" v-model.number="op1" />
        <input type="number" v-model.number="op2" />-->
        <input type="text" v-model="op1" />
        <div class="sign">{{ operator }}</div>
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
      <div class="show-key">
        <input type="checkbox" id="checkbox-key" v-model="checked" />
        <label for="checkbox-key">Keyboard</label>
      </div>
      <div class="functionField">
        <div class="numberField" v-show="checked">
          <button
            v-for="numberKey of calcNumbers"
            :key="numberKey"
            @click="addNumber(numberKey)"
          >
            {{ numberKey }}
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
      op1: "",
      op2: "",
      operator: "",
      result: null,
      picked: "op1",
      checked: false,
      error: "",
      calcNumbers: [1, 2, 3, 4, 5, 6, 7, 8, 9, 0, "<--"],
      operators: ["+", "-", "/", "*", "POW", "DIV"],
    };
  },
  methods: {
    calculate(operator) {
      this.error = "";
      this.operator = operator;
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
    addNumber(numberKey) {
      //console.log(numberKey);
      if (numberKey == "<--") {
        console.log(this[this.picked]);
        this[this.picked] = this[this.picked].slice(0, -1);
      } else this[this.picked] += String(numberKey);
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
      this.result = null;
      this.op1 = "";
      this.op2 = "";
      this.operator = "";
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
  height: 450px;
  .screen {
    margin: 20px auto;
    display: flex;
    justify-content: center;
    width: 350px;
    input {
      text-align: center;
      margin: 15px;
      width: 50px;
      height: 30px;
    }
    .sign {
      margin-top: 20px;
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
      width: 100px;
      height: 30px;
      border: 1px solid black;
    }
  }
  .error {
    color: #f00;
  }
  .functionField {
    display: flex;
    height: 230px;
    .numberField {
      width: 200px;
      margin: 30px auto;
      display: flex;
      justify-content: center;
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
    .calc {
      margin: 30px auto;
      width: 200px;
      height: 100px;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-wrap: wrap;
      button {
        display: block;
        width: 50px;
        height: 50px;
        margin: 5px;
        font-size: 13px;
        font-weight: bold;
      }
    }
  }
  .clear {
    height: 40px;
  }
}
</style>
