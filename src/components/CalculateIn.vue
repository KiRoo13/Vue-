<template>
  <div class="calculate">
    <h1>Калькулятор</h1>
    <div class="calculate_contener">
      <div class="calculate_top">
        <input v-model ="operand1" class="bottom" type="text"> Введите 1 число
        <input v-model ="operand2" type="text"> Введите 2 число
        <span> {{ result }} </span>
        <span v-show="show"> {{ error }} </span>
      </div>
      <div class="calculate_bottom">
        <button @click="step"  class="calculate_btn">Возвести в степень</button>
        <button @click="sum" class="calculate_btn">+</button>
        <button @click="minus" class="calculate_btn">-</button>
        <button @click="um" class="calculate_btn">*</button>
        <button @click="del" v-bind:disabled="isButtonDisabled" class="calculate_btn">/</button>
      </div>
    </div>
  </div>
</template>

<script>
   export default {
    name: "CalculateIn",
    data () {
     return {
       isButtonDisabled: false,
       error: 'Делить на 0 нельзя!',
       show: false,
       result: '',
       operand1: '',
       operand2: ''
      }
    },
    methods: {
      sum (){
        this.result = Number(this.operand1) + Number(this.operand2);
        this.show = false
      },
      minus (){
        this.result = Number(this.operand1) - Number(this.operand2);
        this.show = false
      },
      um (){
        this.result = Number(this.operand1) * Number(this.operand2);
        this.show = false
      },
      del (){
          if (Number(this.operand2) === 0) {
          this.show = true;
          this.isButtonDisabled = true;
          this.result = 0;
        } else if (Number(this.operand2) !== 0){
           this.isButtonDisabled = false;
           this.result = Number(this.operand1) / Number(this.operand2);
        }
      },
      step (){
          this.result = Math.pow(Number(this.operand1), Number(this.operand2));
          this.show = false
        }
    }
   }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.calculate {
      min-width: 300px;
      min-height: 300px;
      background-color: beige;
      box-shadow: 1px 1px 1px black;
}
.calculate_contener {
      margin:  0 auto;
      width: 300px;
      height: 300px;
      padding: 20px;
      display: flex;
      flex-direction: column;
      justify-content: space-evenly;
      align-items: center;
}
.calculate_btn:not(:last-child) {
  margin-right: 10px;
}
input {
  margin-button: 5px;
}
span {
    margin-bottom: 20px;
    font-size: 20px;
    font-weight: bold;
}
h1 {
  padding-top: 10px
}
</style>
