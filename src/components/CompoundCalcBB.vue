<template>
    <body style="text-align:center">
        <form @submit.prevent="calculate" class="main">
            <div>
            <label>loan amount</label>
            <input v-model.number="loanAmount " alignment="center" v-text="center" text-align="center"/>
            </div>
            <div>
            <label>interest rate</label>
            <input v-model.number="interestRate " alignment="center" v-text="center" text-align="center"/>
            </div>
            <div>
            <label>number of months to pay off loan</label>
            <input v-model.number="numMonths " alignment="center" v-text="center" text-align="center"/>
            </div>
            <button @click="Calculate">Calculate monthly payment</button>
            <button type="reset" value="reset">ClearAll</button>
            </form>  
            <p>monthlypayment:{{monthlyPayment.toFixed(2)}}</p>
    </body>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      loanAmount: 0,
      interestRate: 0,
      numMonths: 0,
      monthlyPayment: 0,
    };
  },
  computed: {
    formValid() {
      const { loanAmount, interestRate, numMonths } = this;
      return (
        +loanAmount >= 0 &&
        0 <= +interestRate &&
        +interestRate <= 100 &&
        +numMonths > 0
      );
    },
  },
  methods: {
    calculate() {
      if (!this.formValid) {
        return;
      }
      const { loanAmount, interestRate, numMonths } = this;
      this.monthlyPayment = (loanAmount * (1 + interestRate / 100)) / numMonths;
    },
    ClearAll(){
        this.loanAmount=0
        this.interestRate=0
        this.numMonths=0
        this.monthlyPayment=0
    },
  },
};
</script>

<style>
#outer{width:30%;max-width:600px;background:#fff;margin:0 auto}
#cover{border:2px solid #111;padding:15px 0}
.main{table-layout:fixed;width:94%;border:0;border-collapse:collapse;margin:0 auto}
.main td{padding:0 8px;vertical-align:middle;border:0}
.main input{width:30%;border:1px solid #ccc;margin:2px 0;padding:0 2%;height:22px;text-align:right}.ac{text-align:center}.b{font-weight:bold}
.main select{width:30%;border:1px solid #ccc;margin:2px 0;background:#fff;height:22px}.w50{width:30%}.main button{width:30%;font-weight:bold;margin:3px 0}
</style>