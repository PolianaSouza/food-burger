<template>
    <div class="q-ma-xl q-ma-md">
        <q-table
            title="Gerenciar Pedidos"
            :rows="pedidos"
            :columns="columns"
            row-key="id"
            no-data-label="Não temos pedidos"
        >
            <template v-slot:body-cell-actions="props">
                <q-td :props="props">
                    <q-btn
                        icon="done"
                        color="green-10"
                        dense
                    />
                </q-td>
            </template>
        </q-table>
    </div>
</template>

<script>
import {api} from '../boot/axios'

export default {
    name: 'TablePedidos',
    data(){
        return {
            columns: [
                {
                    name: 'id',
                    label: 'id',
                    align: 'left',
                    field: 'id',
                },
                {
                    name: 'name',
                    label: 'Nome do Cliente',
                    align: 'left',
                    field: 'name',
                },
                {
                    name: 'bread',
                    label: 'Tipo de Pão',
                    align: 'left',
                    field: 'bread',
                },
                {
                    name: 'meat',
                    label: 'Tipo de Carne',
                    align: 'left',
                    field: 'meat',
                },
                {
                    name: 'optional',
                    label: 'Opcionais',
                    align: 'left',
                    field: 'optional',
                },
                {
                    name: 'actions',
                    label: 'Ações',
                    align: 'center',
                    field: 'actions',
                },
            ],
            pedidos: []
        }
    },
    methods: {
        async getBurgers(){
            try {
                const response = await api.get('hamburgueres');
                const data = response.data
                this.pedidos = data;
                console.log(response)
            } catch (error) {
                console.log(error)
            }
        }
    },
    mounted() {
        this.getBurgers()
    }
}
</script>

<style scoped>

</style>