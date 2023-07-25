<script setup>
import { reactive } from 'vue';
import Cabecalho from './components/Cabecalho.vue'
import Calculadora from './components/Calculadora.vue'
import Resultado from './components/Resultado.vue'

  const estado = reactive({
    filtro: 'somatória',
    primeiroNumero: 0,
    segundoNumero: 0,
    
  })

  const calculaSoma = () => {
    const {primeiroNumero, segundoNumero} = estado;
    return  parseInt(primeiroNumero) + parseInt(segundoNumero);
  }

  const calculaSubtracao = () => {
    const {primeiroNumero, segundoNumero} = estado;
    return  parseInt(primeiroNumero) - parseInt(segundoNumero);
  }

  const calculaMutiplicacao = () => {
    const {primeiroNumero, segundoNumero} = estado;
    return  parseInt(primeiroNumero) * parseInt(segundoNumero);
  }

  const calculaDivisao = () => {
    const {primeiroNumero, segundoNumero} = estado;
    return  parseInt(primeiroNumero) / parseInt(segundoNumero);
  }


  const getOperacao = () => {
    const {filtro} = estado;

    switch(filtro) {
      case 'multiplicação':
        return calculaMutiplicacao();
      case 'divisão':
        return calculaDivisao();
      case 'subtração':
        return calculaSubtracao();
      default:
        return calculaSoma();
    }
  }

  const getSimbolo = () => {
    const {filtro} = estado;

    switch(filtro) {
      case 'divisão':
        return "/";
      case 'subtração':
        return "-";
      default:
        return "+";
    }
  }

</script>

<template>
  <div class="container">
    <Cabecalho />
    <Calculadora :getSimbolo="getSimbolo()" :trocar-filtro="evento => estado.filtro = evento.target.value" :primeiroNumero="evento => estado.primeiroNumero = evento.target.value" :segundoNumero="evento => estado.segundoNumero = evento.target.value"/>
    <Resultado :verificar="!isFinite(getOperacao()) || isNaN(getOperacao())" :filtro="estado.filtro"  :getOperacao="getOperacao()" />

  </div>
</template>

<style scoped>

</style>