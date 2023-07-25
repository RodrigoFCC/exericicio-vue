<script setup>
    const props = defineProps(['primeiroNumero', 'segundoNumero', 'getSimbolo', 'trocarFiltro'])
</script>

<template>
    <div>
        <div class="row">
            <div class="col-2">
                <input @keyup="props.primeiroNumero" required type="number"
                    placeholder="Digite um numero" class="form-control">
            </div>
            {{ props.getSimbolo }}
            <div class="col-2">
                <input @keyup="props.segundoNumero" required type="number"
                    placeholder="Digite um numero" class="form-control">
            </div>
            <div class="col-md-2">
                <select @change="props.trocarFiltro" class="form-control">
                    <option value="somatória">Somar</option>
                    <option value="subtração">Subtrair</option>
                    <option value="multiplicação">Multiplicar</option>
                    <option value="divisão">Dividir</option>
                </select>
            </div>
        </div>
    </div>
</template>