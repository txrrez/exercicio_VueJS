<script setup>
import { reactive } from 'vue';

const estado = reactive({
  filtro: '',
  inputSoma1: 0,
  inputSoma2: 0,
  inputSubtracao1: 0,
  inputSubtracao2: 0,
  inputDivisao1: 0,
  inputDivisao2: 0,
  inputMultiplicacao1: 0,
  inputMultiplicacao2: 0,
});

function calculoSoma() {
  return estado.inputSoma1 + estado.inputSoma2;
}

function calculoSubtracao() {
  return estado.inputSubtracao1 - estado.inputSubtracao2;
}

function calculoDivisao() {
  return estado.inputDivisao2 !== 0 ? estado.inputDivisao1 / estado.inputDivisao2 : 'Erro: Divisão por zero';
}

function calculoMultiplicacao() {
  return estado.inputMultiplicacao1 * estado.inputMultiplicacao2;
}

</script>

<template>
  <div class="container">
    <select class="menu" v-model="estado.filtro">
      <option class="opcoes" value="">Escolha a conta que quer fazer</option>
      <option  class="opcoes" value="soma">Para somar  (+)</option>
      <option class="opcoes" value="subtracao">Para subtrair  (-)</option>
      <option class="opcoes" value="divisao">Para dividir  (/)</option>
      <option class="opcoes" value="multiplicacao">Para multiplicar  (*)</option>
    </select>

    <div v-if="estado.filtro === 'soma'">
      <h1>Calculadora de Soma</h1>
      <input v-model.number="estado.inputSoma1" type="number" placeholder="Digite um número" /> <br />
      <input v-model.number="estado.inputSoma2" type="number" placeholder="Digite outro para somar" /> <br />
      <h3>Resultado da soma: </h3> </br> <h4>{{ calculoSoma() }}</h4>
    </div>

    <div v-if="estado.filtro === 'subtracao'">
      <h1>Calculadora de Subtração</h1>
      <input v-model.number="estado.inputSubtracao1" type="number" placeholder="Digite um número" /> <br />
      <input v-model.number="estado.inputSubtracao2" type="number" placeholder="Digite outro para subtrair" /> <br />
      <h3>Resultado da subtração: </h3> </br> <h4>{{ calculoSubtracao() }}</h4>
    </div>

    <div v-if="estado.filtro === 'divisao'">
      <h1>Calculadora de Divisão</h1>
      <input v-model.number="estado.inputDivisao1" type="number" placeholder="Digite um número" /> <br />
      <input v-model.number="estado.inputDivisao2" type="number" placeholder="Digite outro para dividir" /> <br />
      <h3>Resultado da divisão: </h3> </br> <h4>{{ calculoDivisao() }}</h4>
    </div>

    <div v-if="estado.filtro === 'multiplicacao'">
      <h1>Calculadora de Multiplicação</h1>
      <input v-model.number="estado.inputMultiplicacao1" type="number" placeholder="Digite um número" /> <br />
      <input v-model.number="estado.inputMultiplicacao2" type="number" placeholder="Digite outro para multiplicar" />
      <br />
      <h3>Resultado da Multiplicação: </h3> </br> <h4>{{ calculoMultiplicacao() }}</h4>
    </div>
  </div>
</template>

<style scoped>
ul {
  list-style: none;
}

.container{
  padding-top: 30px;
  text-align: center
}

.menu{
  border-radius: 30px;
  min-height: 50px;
}

.opcoes{
  text-align: center;
}

input{
  margin-TOP: 10px;
  border-radius: 30px;
  text-align: center
}

</style>
