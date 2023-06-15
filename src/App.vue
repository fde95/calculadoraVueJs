<script setup>
import { ref, watch } from 'vue';

const valor1 = ref(null);
const valor2 = ref(null);
const operador = ref('+');
const resultado = ref(null);

watch([valor1, valor2, operador], () => {
  switch (operador.value) {
    case '+':
      resultado.value = valor1.value + valor2.value;
      break;
    case '-':
      resultado.value = valor1.value - valor2.value;
      break;
    case '*':
      resultado.value = valor1.value * valor2.value;
      break;
    case '/':
      resultado.value = valor1.value / valor2.value;
      break;
    default:
      resultado.value = null;
  }
});
</script>


<template>
  <div class="container">
    <div class="p-5 mt-5 mb-3 bg-light rounded-3">
      <h1 class="fw-bold">Calculadora Vue JS</h1>
      <p class="fw-bold m-0 mb-2">Instruções:</p>
      <p class="m-0"><b>1º</b> Adicione o primeiro valor;</p>
      <p class="m-0"><b>2º</b> Selecione o operador desejado;</p>
      <p class="m-0"><b>3º</b> Adicione o segundo valor;</p>
      <p class="m-0"><b>4º</b> O resultado será exibido na tela automaticamente;</p>
    </div>
    <div class="row">
      <div class="col">
        <input class="form-control" v-model.number="valor1" type="number" @input="calculate">
      </div>
      <div class="col-md-1">
        <select class="form-control" v-model="operador" @change="calculate">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
      </select>
      </div>
      <div class="col">
        <input class="form-control" v-model.number="valor2" type="number" @input="calculate">
      </div>
    </div>
    <div class="row text-center">
      <div class="col mt-3">
        <h2>Resultado é: </h2>
        <span class="fs-1 fw-bold text-success" v-if="resultado !== null">{{ resultado }}</span>
      </div>
    </div>
  </div>
</template>



<style scoped>

</style>


