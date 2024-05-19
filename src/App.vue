<script setup>
import { reactive } from 'vue';
import Formulario from './components/Formulario.vue';

  const estado = reactive({
    filtro: 'adicao',
    numeroA: 0,
    numeroB: 0,
  })

  function adicao(){
    return estado.numeroA + estado.numeroB;
  }
  function subtracao(){
    return estado.numeroA - estado.numeroB;
  }
  function multiplicacao(){
    return estado.numeroA * estado.numeroB;
  }
  function divisao(){
    return estado.numeroA / estado.numeroB;
  }

  const operacao = () => {
    switch (estado.filtro) {    
      case 'subtracao':
        return subtracao();
      case 'multiplicacao':
        return multiplicacao();
      case 'divisao':
        return divisao();
      default:
        return adicao();
    }
  }

</script>

<template>
  <div class="container">
    <header>
      <h1>Easy Math</h1>
    </header>
    <body>
      <Formulario
        :primeiro-numero="evento => estado.numeroA = Number(evento.target.value)"
        :segundo-numero="evento => estado.numeroB = Number(evento.target.value)"
        :filtra-operacao="evento => estado.filtro = evento.target.value"
      />
      <p>Igual a <span>{{ operacao() }}</span></p>
    </body>
    </div>
</template>

<style scoped>
  
  .container{
    display: flex;
    flex-direction: column;
    height: 100vh;
    justify-content: center;
  }
  
  h1 {
    color: #4CE0D2;
    margin-bottom: 24px
  }

  span {
    background: #136F63;
    color: #FFF;
    padding: 4px;
    border-radius: 8px;
  }

</style>
