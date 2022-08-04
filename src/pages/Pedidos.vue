<template>
    <q-page>
        <table-pedidos />
    </q-page>
</template>

<script>
import TablePedidos from '../components/TablePedidos.vue'

export default {
    name: 'Pedidos',
    components: {
        TablePedidos,
    }
}
</script>