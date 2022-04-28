<template>
    <body>
        <title>"Compound Interest Calculator"</title>
    <section>
        <input placeholder="Principal (P) (INR) " type="number" v-model.number="num1">
        <input placeholder="Interest Rate (R) (%)" type="number" v-model.number="num2">
        <input placeholder="Compound Period (n) (Month)" type="number" v-model.number="num2">
    </section>
    <textarea>{{monthlyPayment}}</textarea>
    <button @click="Calculate">"Calculate Compound Interest"</button> 
    <button @click="Clear">"Clear"</button> 
    </body>
</template>

<script>
export default {
  //name: 'HelloWorld',
  //props: {
    //msg: String
  //},
  data() {
    return {
      P: 0,
      R: 0,
      n: 0,
      monthlyPayment: 0,
    };
  }, 
  computed: {
    formValid() {
      const { P, R, n } = this;
      return (
        +P >= 0 &&
        0 <= +R &&
        +R <= 100 &&
        +n > 0
      );
    },
  },  
  methods: {
    Calculate(){
        if (!this.formValid) {
            return;
        }
        const { P, R, n } = this;
      this.monthlyPayment = (P * (1 + R / 100)) / n;    
    },

    Clear(){
        this.p=0
        this.R=0
        this.n=0
    },  
  },
};
</script>



<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
