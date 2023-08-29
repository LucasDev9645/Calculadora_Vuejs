<script setup>
import { ref, watch } from "vue";

const valor1 = ref(null);
const valor2 = ref(null);
const operador = ref("+");
const resultado = ref(null);

watch([valor1, valor2, operador], () => {
  switch (operador.value) {
    case "+":
      resultado.value = valor1.value + valor2.value;
      break;
    case "-":
      resultado.value = valor1.value - valor2.value;
      break;
    case "*":
      resultado.value = valor1.value * valor2.value;
      break;
    case "/":
      resultado.value = valor1.value / valor2.value;
      break;
    default:
      resultado.value = null;
  }
});
</script>

<template>
  <div>
    <h1>Calculadora</h1>
    <div>
      <div>
        <input v-model.number="valor1" type="number" @input="calculate" />
      </div>
      <div>
        <select v-model="operador" @change="calculate">
          <option value="+">+</option>
          <option value="-">-</option>
          <option value="*">*</option>
          <option value="/">/</option>
        </select>
      </div>
      <div>
        <input v-model.number="valor2" type="number" @input="calculate" />
      </div>
    </div>
    <div>
      <div class="border">
        <h2>Resultado:</h2>
        <span v-if="resultado !== null">{{ resultado }}</span>
      </div>
    </div>
  </div>
</template>

<style scoped>
h1,
h2 {
  color: #8931ff;
}

input {
  text-align: center;
  background-color: #f6f6f6;
  font-weight: 700;
  padding: 1.3rem 0;
  font-size: 2rem;
  border: 2px solid #8931ff;
  border-radius: 0.5rem;
  margin: 0.5rem 0;
}

select {
  padding: 1rem 0.5rem;
  font-size: 2rem;
  border-radius: 0.5rem;
  border: 3px solid #6c00ff;
}

.border {
  margin: 2rem 0;
  background: #f6f6f6;
  font-size: 1.5rem;
  font-weight: 700;
  border-radius: 0.5rem;
  border: 3px solid #6c00ff;
  color: #000000;
}
</style>
