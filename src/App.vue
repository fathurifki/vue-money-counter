<template>
  <div id="app">
    <h1 class="title">Money Counter</h1>
    <div class="columns">
      <div class="column">
        <div class="field">
          <div class="control">
            Dollars:
            <input
              class="input"
              type="number"
              v-model.number="dollar"
               @change="checkNegative"
              min="0"
            />
          </div>
        </div>
      </div>
      <div class="column">
        <div class="field">
          <div class="control">
            Pennies:
            <input class="input" type="number" v-model.number="penny" min="0" @change="checkNegative">
          </div>
        </div>
      </div>
    </div>
    <div class="columns">
      <div class="column">
        <div class="field">
          <div class="control">
            Fives:
            <input class="input" type="number" v-model.number="five" min="0"  @change="checkNegative"/>
          </div>
        </div>
      </div>
      <div class="column">
        <div class="field">
          <div class="control">
            Nickles:
            <input
              class="input"
              type="number"
              v-model.number="nickle"
               @change="checkNegative"
              min="0"
            />
          </div>
        </div>
      </div>
    </div>
    <div class="columns">
      <div class="column">
        <div class="field">
          <div class="control">
            Tens:
            <input
              class="input"
              type="number"
              placeholder="Tens"
              v-model.number="ten"
               @change="checkNegative"
              min="0"
            />
          </div>
        </div>
      </div>
      <div class="column">
        <div class="field">
          <div class="control">
            Dimes:
            <input
              class="input"
              type="number"
              placeholder="Dimes"
              v-model.number="dime"
               @change="checkNegative"
              min="0"
            />
          </div>
        </div>
      </div>
    </div>
    <div class="columns">
      <div class="column">
        <div class="field">
          <div class="control">
            Twenties:
            <input
              class="input"
              type="number"
              placeholder="Twenties"
              v-model.number="twenty"
               @change="checkNegative"
              min="0"
            />
          </div>
        </div>
      </div>
      <div class="column">
        <div class="field">
          <div class="control">
            Quarters:
            <input
              class="input"
              type="number"
              placeholder="Quarters"
              v-model.number="quarter"
               @change="checkNegative"
              min="0"
            />
          </div>
        </div>
      </div>
    </div>
    <div class="columns">
      <div class="column">
        <div class="field">
          <div class="control">
            Fifties:
            <input
              class="input"
              type="number"
              placeholder="Fifties"
              v-model.number="fifty"
               @change="checkNegative"
              min="0"
            />
          </div>
        </div>
      </div>
      <div class="column has-text-left">
        <p>Total Bills: ${{ totalBills() }}</p>
        <p>Total Coins: ${{ totalCoins() }}</p>
        <p>Total: ${{ result() }}</p>
        <!-- <p>Total: ${{ total() }}</p>   -->
      </div>
    </div>
    <div class="columns">
      <div class="column">
        <div class="field">
          <div class="control">
            Hundreds:
            <input
              class="input"
              type="number"
              placeholder="Hundreds"
               @change="checkNegative"
              v-model.number="hundred"
            />
          </div>
        </div>
      </div>
      <div class="column">
        <button class="button is-info is-rounded is-fullwidth" @click="reset">
          <span class="icon">
            <i class="fas fa-undo"></i>
          </span>
          <span>Reset</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      dollar: "0",
      five: "0",
      ten: "0",
      twenty: "0",
      fifty: "0",
      hundred: "0",
      penny: "0",
      nickle: "0",
      dime: "0",
      quarter: "0",
    };
  },
  methods: {
    totalBills() {
      const totalDollar = parseInt(this.dollar) * 1;
      const totFive = parseInt(this.five) * 5;
      const totTen = parseInt(this.ten) * 10;
      const totTwenty = parseInt(this.twenty) * 20;
      const totFifty = parseInt(this.fifty) * 50;
      const totHundred = parseInt(this.hundred) * 100;
      const total =
        totalDollar +
        totFive +
        totFive +
        totTwenty +
        totTen +
        totFifty +
        totHundred;
      return Math.round(total * 100) / 100;
    },
    totalCoins() {
      const totPenny = parseInt(this.penny) * 0.01;
      const totNickle = parseInt(this.nickle) * 0.05;
      const totDime = parseInt(this.dime) * 0.1;
      const totQuarter = parseInt(this.quarter) * 0.25;
      const total = totPenny + totNickle + totDime + totQuarter;
      return Math.round(total * 100) / 100;
    },
    result() {
      return this.totalBills() + this.totalCoins();
    },
    reset() {
      this.dollar = "0";
      this.five = "0";
      this.ten = "0";
      this.twenty = "0";
      this.fifty = "0";
      this.hundred = "0";
      this.penny = "0";
      this.nickle = "0";
      this.dime = "0";
      this.quarter = "0";
    },
    checkNegative() {
        if (this.dollar < 0){
          this.dollar = 0;
        }
        if (this.five < 0){
          this.five = 0;
        }
        if(this.ten < 0 ){
          this.ten = 0;
        }
        if (this.twenty < 0){
          this.twenty = '0';
        }
        if (this.fifty < 0){
          this.fifty = '0';
        }
        if (this.hundred < 0){
          this.hundred = '0';
        }
        if (this.penny < 0){
          this.penny = '0';
        }
        if (this.nickle < 0){
          this.nickle = '0';
        }
        if (this.dime < 0){
          this.dime = '0';
        }
        if (this.quarter < 0){
          this.quarter = '0';
        }
      }
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
