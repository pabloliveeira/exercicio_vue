<script setup>
  import { reactive } from 'vue';
  import Cabecalho from './components/Cabecalho.vue';
  import Formulario from './components/Formulario.vue';

  const estado = reactive({
    filtro: 'somar',
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
    return estado.numero1 / estado.numero2
  }

  const multiplica = () => {
    return estado.numero1 * estado.numero2
  }

  const subtrai = () => {
    return estado.numero1 - estado.numero2
  }

  const soma = () => {
    return estado.numero1 + estado.numero2
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
    <Cabecalho/>
    <Formulario :resultado="resultado()" :operador1="evento => estado.numero1 = parseFloat(evento.target.value)" :operador2="evento => estado.numero2 = parseFloat(evento.target.value)" :filtro-tarefa="evento => estado.filtro = evento.target.value" />
  </div>
</template>

<style scoped>

</style>
