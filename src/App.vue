<script setup>
import { reactive } from 'vue';

  const estado = reactive({
    numero1: 0,
    numero2: 0,
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
    return numero1 / numero2
  }

  const multiplica = () => {
    return numero1 * numero2
  }

  const subtrai = () => {
    return numero1 - numero2
  }

  const soma = () => {
    return numero1 + numero2
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
        <div class="col-2">
          <span>{{ resultado() }}</span>
        </div>
      </div>
    </form>
  </div>
</template>

<style scoped>

</style>
