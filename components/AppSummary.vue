<template>
    <v-card
        variant="tonal"
        class="summary d-flex flex-column ga-10"
    >
        <h1>Resumo</h1>
        <v-table 
            density="compact"
            class="table-summary"
        >
            <tbody>
                <tr>
                    <td>Quantidade:</td>
                    <td>{{ quantity }}</td>
                </tr>
                <tr>
                    <td>Preço:</td>
                    <td>R$ {{ price }}</td>
                </tr>
                <tr>
                    <td>Frete:</td>
                    <td>R$ {{ freightCharges }}</td>
                </tr>
                <tr class="total">
                    <td>Total:</td>
                    <td>R$ {{ total }}</td>
                </tr>
            </tbody>
        </v-table>
        <p>Ao concluir sua compra você concorda com nossos <span>Termos de Serviço</span></p>
        <v-btn class="button">
            Finalizar compra
        </v-btn>
    </v-card>
</template>

<script setup>

// const props = defineProps({
//   quantity: number
//   price: numbe
//   freightCharges: number
// });

const props = defineProps({
    quantity,
    price,
    freightCharges
})

const total = computed(() => {
  return (props.price * props.quantity) + props.freightCharges
});

</script>

<style scoped>
.summary {
    color: #1f855a;
    padding: 50px;
    width: 20vw;
}

.summary h1 {
    color: #00FF95;
}

.table-summary {
    width: 15vw;
    background-color: rgba(0, 0, 0, 0); 
    border: none;
}

.button {
    background-color: #bc01d4; 
    
}

.total {
    font-size: 16px;
    font-weight: 900;
    color: #e100ff;     
}

p {
    text-align: center;
    font-size: 13px;
}

span {
    font-weight: 900;
    color: #00FF95;
}
</style>