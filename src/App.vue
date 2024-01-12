<script setup>
import { reactive } from 'vue';

const estado = reactive({
  num1: 0,
  num2: 0,
  operacao: 'adicao',
})

const somar = () => parseFloat(estado.num1) + parseFloat(estado.num2);

const subtrair = () => parseFloat(estado.num1) - parseFloat(estado.num2);

const multiplicar = () => parseFloat(estado.num1) * parseFloat(estado.num2);

const dividir = () => parseFloat(estado.num1) / parseFloat(estado.num2);

function mostraResultado() {
  const { operacao } = estado;

  switch (operacao) {
    case 'adicao':
      return somar();
    case 'subtracao':
      return subtrair();
    case 'multiplicacao':
      return multiplicar();
    case 'divisao':
      return dividir();
  }
  
}

</script>

<template>
  <div class="container text-center bg-light rounded-4 pb-4">
    <h1 class="mt-5 pt-3">Calculadora Aritmética</h1>
    <div class="form">
      <h4 class="">Escolha uma operação:</h4>
      <select @change="evento => estado.operacao = evento.target.value" class="form-control-sm">
        <option value="adicao">Adição</option>
        <option value="subtracao">Subtração</option>
        <option value="divisao">Divisão</option>
        <option value="multiplicacao">Multiplicação</option>
      </select>
      <h5 class="mt-3 mb-3">Insira os números nos campos abaixo para realizar a operação</h5>
      <input @keyup="evento => estado.num1 = evento.target.value" class="col-md-1 me-2" type="number" id="">
      <input  @keyup="evento => estado.num2 = evento.target.value" class="col-md-1 ms-2" type="number" id="">
      <h5 class="mt-3">Resultado:</h5>
      <h1>{{ mostraResultado() }}</h1>
    </div>
  </div>
</template>

<style scoped>

</style>
