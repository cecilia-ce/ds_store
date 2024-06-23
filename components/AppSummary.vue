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
                    <td>
                        <input 
                            v-model="quantity"
                            type="number" 
                            id="quantity" 
                            name="quantity" 
                            min="1" 
                            step="1" 
                            required
                            class="input"
                        />
                    </td>
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

    const props = defineProps(['price', 'freightCharges'])

    const quantity = ref(1)

    const total = computed(() => {
        let totalPrice = (props.price * quantity.value) + props.freightCharges
        return totalPrice.toFixed(2)
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

.input {
    background-color: #0d3121;
    margin-left: 5px;
    width: 50px;
    border-radius: 5px;
    border: none;
    padding-left: 15px;
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