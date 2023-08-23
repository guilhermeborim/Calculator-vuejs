<script setup>
import { reactive } from 'vue';

  const estado = reactive ({
    operator: '+',
    operacao: 
      {
        number1: '',
        number2: '',
        result: '',
      }
  })

  const calculate = () => {
    const { operator } = estado;

    switch(operator) {
      case '+':
        return estado.operacao.result = estado.operacao.number1 + estado.operacao.number2;
      case '-':
        return estado.operacao.result = estado.operacao.number1 - estado.operacao.number2;
      case '*':
        return estado.operacao.result = estado.operacao.number1 * estado.operacao.number2;
      case '/':
        return estado.operacao.result = estado.operacao.number1 / estado.operacao.number2;
    }
}
</script>

<template>
  <div class="calculator">
    <input v-model="estado.operacao.number1" type="number" @keyup="calculate" />
    <select v-model="estado.operator" @change="calculate">
      <option value="+">+</option>
      <option value="-">-</option>
      <option value="*">*</option>
      <option value="/">/</option>
    </select>
    <input v-model="estado.operacao.number2" type="number" @keyup="calculate" />
    <div class="result">Resultado: {{ estado.operacao.result }} </div>
  </div>
</template>

<style scoped>
  .calculator {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    width: 800px;
    height: 800px;
    margin: 0 auto;
  }
  input {
    margin-bottom: 15px;
    margin-top: 15px;
  }
  select {
    width: 50px;
    padding: 5px;
  }
</style>
