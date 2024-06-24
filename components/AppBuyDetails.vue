<template>
    <v-card
        variant="text"
        class="summary"
    >
        <h1>Detalhes da compra</h1>
        <v-table 
            density="compact"
            class="table-summary"
        >
            <tbody>
                <tr>
                    <td>Produto:</td>
                    <td>nome do produto</td>
                </tr>
                <tr>
                    <td>Quantidade:</td>
                    <td>2</td>
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
    </v-card>
</template>

<script setup>

const props = defineProps(['buyDetails'])

</script>

<style scoped>
.summary {
    display: flex;
    flex-direction: column;
    gap: 40px;
    padding: 50px;
}

.summary h1 {
    font-size: 24px;
    color: #1f855a;
}

.table-summary {
    width: 100%;
    background-color: rgba(0, 0, 0, 0); 
    border: none;
    font-size: 18px;
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

@media (max-width: 1400px) {
  .summary {
    width: 80vw;
  }
 
}


</style>