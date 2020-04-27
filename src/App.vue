<template>
  <div id="app">
    <div class="calculator card">

    <input type="text" class="calculator-screen z-depth-1" :value="toCalculate" disabled />

    <div class="calculator-keys">

      <button type="button" class="operator btn btn-info"
      @click="addToCalc('+')" value="+">+</button>
      <button type="button" class="operator btn btn-info"
      @click="addToCalc('-')" value="-">-</button>
      <button type="button" class="operator btn btn-info"
      @click="addToCalc('*')" value="*">&times;</button>
      <button type="button" class="operator btn btn-info"
      @click="addToCalc('/')" value="/">&divide;</button>

      <button type="button" @click="addToCalc('7')"
      value="7" class="btn btn-light waves-effect">7</button>
      <button type="button" @click="addToCalc('8')"
      value="8" class="btn btn-light waves-effect">8</button>
      <button type="button" @click="addToCalc('9')"
      value="9" class="btn btn-light waves-effect">9</button>


      <button type="button" @click="addToCalc('4')"
      value="4" class="btn btn-light waves-effect">4</button>
      <button type="button" @click="addToCalc('5')"
      class="btn btn-light waves-effect">5</button>
      <button type="button" @click="addToCalc('6')"
      value="6" class="btn btn-light waves-effect">6</button>


      <button type="button" @click="addToCalc('1')"
      value="1" class="btn btn-light waves-effect">1</button>
      <button type="button" @click="addToCalc('2')"
      value="2" class="btn btn-light waves-effect">2</button>
      <button type="button" @click="addToCalc('3')"
      value="3" class="btn btn-light waves-effect">3</button>


      <button type="button" @click="addToCalc('0')"
      value="0" class="btn btn-light waves-effect">0</button>
      <button type="button" class="decimal function btn btn-secondary"
      @click="addToCalc('.')" value=".">.</button>
      <button type="button" class="all-clear function btn btn-danger btn-sm"
      @click="cleanCalc()" value="all-clear">AC</button>

      <button type="button" class="equal-sign operator btn btn-default"
      @click="calculateFinal()" value="=">=</button>

    </div>
  </div>
  </div>
</template>

<script>
/* eslint-disable no-eval */
export default {
  name: 'App',
  data() {
    return {
      calculate: [],
      toCalculate: '',
      sumCalc: '',
    };
  },
  methods: {
    calculateFinal() {
      this.sumCalc = eval(this.toCalculate);
      this.toCalculate = this.sumCalc;
      this.calculate.splice(0, this.calculate.length);
      this.calculate.push(this.sumCalc);
    },
    addToCalc(i) {
      if (this.calculate.includes(i) && (i === '+' || i === '-' || i === '*' || i === '/' || i === '.')) {
        this.toCalculate = this.calculate.join('');
      } else {
        this.calculate.push(i);
        this.toCalculate = this.calculate.join('');
      }
    },
    cleanCalc() {
      this.calculate.splice(0, this.calculate.length);
      this.toCalculate = '';
    },
  },
};
</script>

<style>
html {
      font-size: 62.5%;
      box-sizing: border-box;
    }

    *,
    *::before,
    *::after {
      margin: 0;
      padding: 0;
      box-sizing: inherit;
    }

    .calculator {
      border: 1px solid #ccc;
      border-radius: 10px;
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      width: 350px;
    }

    .calculator-screen {
      width: 100%;
      height: 80px;
      border: none;
      background-color: #FBE8A6;
      color: #303C6C;
      text-align: right;
      padding-right: 20px;
      padding-left: 10px;
      font-size: 4rem;
    }

    button {
      height: 60px;
      font-size: 2rem!important;
      background-color: #B4DFE5;
    }

    .equal-sign {
      height: 100%;
      grid-area: 2 / 4 / 6 / 5;
    }

    .calculator-keys {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      grid-gap: 20px;
      padding: 20px;
      background-color: #F4976C;
    }
</style>
