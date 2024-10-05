<script setup>
import { reactive } from 'vue';

const estado = reactive({
  number1: null,
  number2: null,
  filtro: 'add',
  resultado: null,
});

const calcular = () => {
  switch (estado.filtro) {
    case 'mult':
      estado.resultado = estado.number1 * estado.number2;
      break;

    case 'add':
      estado.resultado = estado.number1 + estado.number2;
      break;

    case 'sub':
      estado.resultado = estado.number1 - estado.number2;
      break;

    case 'div':
      estado.resultado = estado.number2 !== 0 ? estado.number1 / estado.number2 : 'Erro (divisão por zero)';
      break;
  }
};
</script>

<template>
  <div class="box">
    <div class="container">
      <h1>Calculadora</h1>
      <h3>Como deseja fazer seu cálculo?</h3>

      <select v-model="estado.filtro">
        <option value="add">Adição</option>
        <option value="sub">Subtração</option>
        <option value="mult">Multiplicação</option>
        <option value="div">Divisão</option>
      </select>

      <form @submit.prevent>
        <input
          type="number"
          required
          v-model.number="estado.number1"
          placeholder="Digite o N.1"
          @keyup="calcular"
        >
        <input
          type="number"
          required
          v-model.number="estado.number2"
          placeholder="Digite o N.2"
          @keyup="calcular"
        >
      </form>
    </div>
    <div class="line"></div>
    <div class="container">
      <h2>Resultado: {{ estado.resultado }}</h2>
    </div>
  </div>
</template>

