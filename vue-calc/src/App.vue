<script setup>
import { reactive, computed } from 'vue'

const state = reactive({
  number1: 0,
  number2: 0,
  operation: '+'
})

const result = computed(() => {
  const n1 = parseFloat(state.number1) || 0;
  const n2 = parseFloat(state.number2) || 0;

  switch (state.operation) {
    case '+':
      return n1 + n2;
    case '-':
      return n1 - n2;
    case '*':
      return n1 * n2;
    case '/':
      if (n2 === 0) {
        return 'Erro: Divisão por 0';
      }
      return n1 / n2;
    default:
      return 0;
  }
})
</script>

<template>
  <div class="calculator">
    <h1>Calculadora Aritmética Vue.js</h1>
    
    <input type="number" v-model.number="state.number1">
    
    <select v-model="state.operation">
      <option value="+">+</option>
      <option value="-">-</option>
      <option value="*">*</option>
      <option value="/">/</option>
    </select>
    
    <input type="number" v-model.number="state.number2">
    
    <hr>
    <h2>Resultado: {{ result }}</h2>
  </div>
</template>

<style>
body {
  font-family: Arial, sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background-color: #f4f4f4;
}

.calculator {
  max-width: 500px;
  margin: 20px auto;
  padding: 25px;
  border-radius: 8px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  background-color: #fff;
  text-align: center;
}

input, select {
  font-size: 1.5rem;
  padding: 10px;
  margin: 0 10px;
  width: 120px;
  text-align: center;
}

select {
  width: 60px;
}

h1 {
  color: #2c3e50;
}

h2 {
  font-size: 2rem;
  color: #42b983;
  min-height: 40px;
}
</style>