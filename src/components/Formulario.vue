<script setup>

    const props = defineProps(['primeiroNumero', 'segundoNumero', 'filtraOperacao'])

</script>

<template>
    
    <form>
        <input @keyup="props.primeiroNumero" type="number" placeholder="insira o numero">
        <select @change="props.filtraOperacao" class="form-control">
            <option value="adicao">mais</option>
            <option value="subtracao">menos</option>
            <option value="multiplicacao">vezes</option>
            <option value="divisao">dividido por</option>
        </select>
        <input @keyup="props.segundoNumero" type="number" placeholder="insira o numero">
      </form>

</template>

<style scoped>

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
    
</style>