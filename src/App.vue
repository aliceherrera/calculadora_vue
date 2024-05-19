<script setup>
import { reactive } from 'vue';

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
      <form>
          <input @keyup="evento => estado.numeroA = evento.target.value" type="number" placeholder="insira o numero">
          <select @change="evento => estado.filtro = evento.target.value" class="form-control">
            <option value="adicao">mais</option>
            <option value="subtracao">menos</option>
            <option value="multiplicacao">vezes</option>
            <option value="divisao">dividido por</option>
          </select>
          <input @keyup="evento => estado.numeroB = evento.target.value" type="number" placeholder="insira o numero">
        </form>
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

  form input,
  select {
    display: flex;
    margin-bottom: 8px;
    background: #136F63;
    color: #FFF;
    height: 32px;
    border-radius: 8px;
    border-style: hidden;
    padding-left: 8px;
    padding-right: 8px;
    padding-bottom: 4px;
    max-width: 200px;
    width: 100%;
  }

  ::placeholder{
    color: #FFF;
  }

  span {
    background: #136F63;
    color: #FFF;
    padding: 4px;
    border-radius: 8px;
  }

</style>
