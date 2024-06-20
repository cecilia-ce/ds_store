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
                    <td>1</td>
                </tr>
                <tr>
                    <td>Preço:</td>
                    <td>R$ 58,50</td>
                </tr>
                <tr>
                    <td>Frete:</td>
                    <td>R$ 30,00</td>
                </tr>
                <tr class="total">
                    <td>Total:</td>
                    <td>R$ 88,50</td>
                </tr>
            </tbody>
        </v-table>
        <p>Ao concluir sua compra você concorda com nossos <span>Termos de Serviço</span></p>
        <v-btn class="button">
            Finalizar compra
        </v-btn>
    </v-card>
</template>

<style scoped>
.summary {
    color: #1f855a;
    padding: 50px;
    width: 20vw;
}

.table-summary {
    width: 15vw;
    background-color: rgba(0, 0, 0, 0); 
    border: none;
}

.button {
    background-color: #74447a; 
    
}

.total {
    font-size: 16px;
    font-weight: 900;
    color: #74447a;  
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