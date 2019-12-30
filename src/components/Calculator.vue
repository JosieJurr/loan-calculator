<template>
<div class="app">
    <div class="monthly-cost">
        <span class="label monthly-cost--label">
            Månadskostnad
        </span>
        <span class="monthly-cost--value">
        <!-- monthlyCost + monthlyCostSuffix -->
        2173 kr
        </span>
    </div>

    <div class="amount">
        <span class="label amount--label">
            <!-- loanAmountLabel -->
            Lånebelopp
        </span>
        <div >
            <button class="button calculator-button">
                <span>-</span>
            </button>

            <input class="input amount--value" value="250 000 kr">

            <button class="button calculator-button">
                <span>+</span>
            </button>
        </div>
    </div>

    <div class="repayment">
        <span class="label repayment--label">
            Återbetalningstid
        </span>

        <div>
            <button class="button calculator-button">
                <span>-</span>
            </button>

            <input class="input repayment--value" value="14 år">

            <button class="button calculator-button">
                <span>+</span>
            </button>
        </div>
    </div>
    <div class="cta">
        <button class="button cta-button">
            <!-- ctaLabel -->
            Ansök nu
        </button>
    </div>
</div>
</template>

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
    max-width: 20rem;
    font-family: "UV Sharp Sans No1 Book";
}
.label {
    display: block;
    padding-bottom: 0.4rem;
}
.button {
    background: #61d5a7;
    border: none;
    font-size:15px;
    color: #FFF;
    border-radius: 30px;
    width: 15rem;
    height: 3rem;
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

</style>
