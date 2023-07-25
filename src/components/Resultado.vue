<script setup>
        const props = defineProps(['verificar', 'getOperacao', 'filtro'])

</script>

<template>
     <div>
        <h3 class="mt-4" v-if="props.verificar">
            Não é possível fazer essa operação, tente outros números
        </h3>
        <h3 class="mt-4" v-else>
            O resultado desta {{ props.filtro }} é {{ props.getOperacao }}
        </h3>
    </div>
</template>