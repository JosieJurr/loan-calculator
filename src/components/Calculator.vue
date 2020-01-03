<template>
  <div class='app' id='app'>
    <div class='monthly-cost'>
      <span class='label'>
        {{ monthlyCostLabel }}
      </span>
      <span class='monthly-cost--value'>
        <!-- monthlyCost + monthlyCostSuffix -->
        {{ monthlyCost() }} {{ loanAmountSuffix }}
      </span>
    </div>

    <div class='amount'>
      <span class='label'>
        {{loanAmountLabel}}
      </span>
      <div>
        <button class='button calculator-button' v-on:click="amountDecrease()">
          <span class="icon">-</span>
        </button>

        <input class='input amount--value' v-model.number='loanAmount' :onKeyup='loanEnforceMinMax()'>

        <button class='button calculator-button' v-on:click="amountIncrease()">
          <span class="icon">+</span>
        </button>
      </div>
    </div>
    <div class='repayment'>
      <span class='label'>
        {{repaymentYearsLabel}}
      </span>

      <div>
        <button class='button calculator-button' v-on:click="repaymentDecrease()">
          <span class="icon">-</span>
        </button>
        <input class='input repayment--value' :id='repaymentYearsSuffix' v-model.number='repaymentYears' :onKeyup='repaymentEnforceMinMax()'>
        <button class='button calculator-button' v-on:click="repaymentIncrease()">
          <span class="icon">+</span>
        </button>
      </div>
    </div>
    <div class='cta'>
      <button class='button cta-button'>
        {{ctaLabel}}
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    monthlyCostLabel: 'Månadskostnad',
    monthlyCostSuffix: 'kr',
    loanAmountLabel: 'Lånebelopp',
    loanAmountMin: 6000,
    loanAmountMax: 600000,
    loanAmount: 250000,
    loanAmountSuffix: 'kr',
    repaymentYearsLabel: 'Återbetalningstid',
    repaymentYears: 14,
    repaymentYearsMin: 1,
    repaymentYearsMax: 15,
    repaymentYearsSuffix: 'år',
    ctaLabel: 'Ansök nu',
    interest: 5.77
  }),
  methods: {
    amountDecrease: function (event) {
      this.loanAmount = this.loanAmount - 5000
    },
    amountIncrease: function (event) {
      this.loanAmount = this.loanAmount + 5000
    },
    repaymentDecrease: function (event) {
      this.repaymentYears = this.repaymentYears - 1
    },
    repaymentIncrease: function (event) {
      this.repaymentYears = this.repaymentYears + 1
    },
    monthlyCost: function (event) {
      var months = this.repaymentYears * 12
      return Math.round(this.loanAmount * (this.interest / 100) / 12 / (1 - Math.pow(1 + (this.interest / 100) / 12, (months * -1))))
    },
    loanEnforceMinMax: function () {
      if (this.loanAmount < this.loanAmountMin) {
        this.loanAmount = this.loanAmountMin
      }
      if (this.loanAmount > this.loanAmountMax) {
        this.loanAmount = this.loanAmountMax
      }
    },
    repaymentEnforceMinMax: function () {
      if (this.repaymentYears < this.repaymentYearsMin) {
        this.repaymentYears = this.repaymentYearsMin
      }
      if (this.repaymentYears > this.repaymentYearsMax) {
        this.repaymentYears = this.repaymentYearsMax
      }
    }
  }
}
</script>

<style>
@font-face {
  font-family: 'UV Sharp Sans No1 Book';
  src: url('../assets/fonts/UV-SharpSansNo1-Book.woff') format('woff');
  font-weight: normal;
  font-style: normal;
}
.app {
  margin: auto;
  padding-top: 5rem;
  max-width: fit-content;
  font-family: 'UV Sharp Sans No1 Book';
}
.label {
  display: block;
  padding-bottom: 0.4rem;
}
.button {
  background: #61d5a7;
  border: none;
  font-size: 15px;
  color: #fff;
  border-radius: 30px;
  height: 3rem;
  width: -webkit-fill-available;
}
.calculator-button {
  height: 44px;
  width: 44px;
  background: #61d5a7;
  border-radius: 50%;
  font-size: 40px;
  font-weight: lighter;
  vertical-align: middle;
  line-height: 1;
}
.icon {
  margin-top: -5px;
  display: block;
}
.input {
  height: 40px;
  font-size: 14px;
  font-weight: 200;
  padding-left: 15px;
  border-radius: 5px;
  border: 1px solid #c8cfd6;
}
.monthly-cost {
  padding-bottom: 1.3rem;
}
.monthly-cost--value {
  font-size: 20px;
}
.amount {
  padding-bottom: 1rem;
}
.repayment {
  padding-bottom: 2rem;
}
button:focus {outline:0;}
input:focus {outline:0;}
input[type=number]::-webkit-inner-spin-button,
input[type=number]::-webkit-outer-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
</style>
