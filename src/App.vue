<script setup>
import { reactive } from 'vue';

  const estado = reactive({
    numero1: document.getElementById("numero-1"),
    numero2: document.getElementById("numero-2"),
    operacoes: [
      {
        titulo: 'somar',
      },
      {
        titulo: 'subtrair',
      },
      {
        titulo: 'multiplicar',
      },
      {
        titulo: 'dividir',
      }
    ]
  })

  const divide = () => {
    return numero1.value / numero2.value
  }

  const multiplica = () => {
    return numero1.value * numero2.value
  }

  const subtrai = () => {
    return numero1.value - numero2.value
  }

  const soma = () => {
    return numero1.value + numero2.value
  }
  
  const resultado = () => {
    const { filtro } = estado;

    switch (filtro) {
      case 'somar':
        return soma();
      case 'subtrair':
        return subtrai();
      case 'multiplicar':
        return multiplica();
      case 'dividir':
        return divide();
    }
    
  }



</script>

<template>
  <div class="container">
    <header class="p-5 mb-2 mt-4">
      <h1>Calculadora Aritmética</h1>
    </header>
    <form prevent>
      <div class="row">
        <div class="col-1">
          <input @change="evento => estado.numero1 = evento.target.value" id="numero-1" class="form-control" type="number" min="0">
        </div>
        <div class="col-1">
          <input @change="evento => estado.numero2 = evento.target.value" id="numero-2" class="form-control" type="number" min="0">
        </div>
        <div class="col-md-2">
          <select @change="evento => estado.operacoes = evento.target.value" class="form-control">
            <option value="somar">Somar</option>
            <option value="subtrair">Subtrair</option>
            <option value="multiplicar">Multiplicar</option>
            <option value="dividir">Dividir</option>
          </select>
        </div>
        <span class="mt-5 fs-2">RESULTADO: {{ resultado() }}</span>
      </div>
    </form>
  </div>
</template>

<style scoped>

</style>
