<script setup>
import { ref, computed } from 'vue';

const numero1 = ref(0);
const numero2 = ref(0);
const operacao = ref('+');

const resultadoCalculado = computed(() => {
  switch (operacao.value) {
    case '+':
      return numero1.value + numero2.value;
    case '-':
      return numero1.value - numero2.value;
    case '*':
      return numero1.value * numero2.value;
    case '/':
      return numero2.value !== 0 ? numero1.value / numero2.value : 'Erro (Divisão por zero)';
    default:
      return 0;
  }
});
</script>

<template>
  <div class="calculadora">
    <h1>Calculadora Aritmética</h1>
    
    <div class="campos">
      <input type="number" v-model.number="numero1" placeholder="Insira o 1º número" />
      
      <select v-model="operacao">
        <option value="+">Somar (+)</option>
        <option value="-">Subtrair (-)</option>
        <option value="*">Multiplicar (*)</option>
        <option value="/">Dividir (/)</option>
      </select>
      
      <input type="number" v-model.number="numero2" placeholder="Insira o 2º número" />
    </div>

    <div class="resultado">
      <h2>Resultado: {{ resultadoCalculado }}</h2>
    </div>
  </div>
</template>

<style scoped>
.calculadora {
  font-family: Arial, sans-serif;
  max-width: 500px;
  margin: 50px auto;
  text-align: center;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
  box-shadow: 2px 2px 10px rgba(0,0,0,0.1);
}

.campos {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin-bottom: 20px;
}

input, select {
  padding: 10px;
  font-size: 16px;
  border-radius: 4px;
  border: 1px solid #999;
}

.resultado {
  background-color: #f0f8ff;
  padding: 10px;
  border-radius: 4px;
}
</style>