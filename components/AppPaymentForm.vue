<template>
    <div class="card">
        <input type="text" />
        <h3 class="mb-5">Informações de Pagamento</h3>
        <div 
            class="payment-card pa-10"
        >
            <v-radio-group 
                v-for="(button, index) in radioButtons" 
                :key="button.id"
                v-model="radios"
            >
                <v-radio color="#bc01d4" :value="button.value" :label="button.label"></v-radio>
            </v-radio-group>


            <!-- pix form -->
            <v-card
                v-if="valuePayment == 1"
                variant="elevated"
                class="pix-card pa-5"
            >
                <h1>Pix</h1>
                <v-divider />
                <p class="my-3">
                    Como pagar com o Pix? Ao finalizar a compra, será gerado um QR Code de pagamento. 
                    Use o aplicativo do seu banco ou carteira digital para escaneá-lo e realizar o pagamento.
                </p>
                <div class="d-flex align-center justify-space-between ga-5">
                    <v-text-field 
                        label="CPF*"
                        :rules="[requiredRule]"
                        placeholder="000.000.000-00"
                        density="compact"
                        type="text"
                        class="mt-3"
                    />
                </div>
            </v-card>

            <!-- credit card form  -->

            <v-card
                v-if="valuePayment == 2"
                variant="elevated"
                class="pix-card pa-5"
            >
                <h1>Insira os dados do Cartão de Crédito</h1>
                
                <v-divider />

                <div class="d-flex flex-row my-5">

                    <div v-for="(icon, index) in iconsPayment" :key="icon.id">
                        <img 
                            :src="icon.src" 
                            :alt="'Payment icon ' + (index + 1)"
                            class="icons-payment"  
                        />
                    </div>

                </div>
                
                <v-text-field 
                    label="Nome do titular*" 
                    :rules="[requiredRule]"
                />
                <v-text-field 
                    label="Número do cartão*" 
                    :rules="[requiredRule]"
                />
                <div class="d-flex flex-row ga-3">
                    <v-text-field 
                        label="Data de vencimento*" 
                        :rules="[requiredRule]"
                    />
                    <v-text-field 
                        label="Código de segurança*" 
                        :rules="[requiredRule]"
                    />
                </div>
                
                <div class="d-flex ga-5">
                    <v-select 
                        :items="installment"
                        label="Parcelas" 
                    />

                    <v-text-field 
                        label="CPF*"  
                        placeholder="000.000.000.00"
                        type="text"
                    />
                </div>
            </v-card>

            <!-- Boleto form -->

            <v-card
                v-if="valuePayment == 3"
                variant="elevated"
                class="pix-card pa-5"
            >
                <h1>Boleto</h1>
                <v-divider />
                <p class="my-3">
                    Ao selecionar <span>Finalizar compra</span> você verá o boleto na tela e terá 3 dias para efetuar o pagamento.
                </p>
                <div class="d-flex align-center justify-space-between ga-5">
                    <v-text-field 
                        label="CPF*"  
                        placeholder="000.000.000-00"
                        density="compact"
                        type="text"
                        class="mt-3"
                    />
                </div>
            </v-card>
        </div>
    </div>
</template>


<script setup>

const props = defineProps(['productValue'])

const radios = ref(null);

const valuePayment = ref(null);

const installment =['1x','2x', '3x', '4x', '5x']

const requiredRule = inputValue => !!inputValue || 'Este campo é obrigatório'

watch(radios, (newVal) => {
    valuePayment.value = newVal;
});

const iconsPayment = [
    {
        id: 1,
        src: '/images/icon-payment1.png'
    },
    {
        id: 2,
        src: '/images/icon-payment2.png'
    },
    {
        id: 3,
        src: '/images/icon-payment3.png'
    },
    {
        id: 4,
        src: '/images/icon-payment4.png'
    },
    {
        id: 5,
        src: '/images/icon-payment5.png'
    },
    {
        id: 6,
        src: '/images/icon-payment6.png'
    },
]

const radioButtons = [
    {
        id: 1,
        value: 1,
        label: 'Pix'
    },
    {
        id: 2,
        value: 2,
        label: 'Cartão de crédito'
    },
    {
        id: 3,
        value: 3,
        label: 'Boleto'
    }
]
</script>

<style scoped>

.payment-card {
    border: solid 2px #1f855a33;
    border-radius: 5px;
}

.text-container{
    width: 80%;
}

.pix-card {
    width: 50vw;
}

.pix-card h1 {
    color: #e100ff; 
}

.button {
    background-color: #bc01d4; 
}

.icons-payment {
    width: 75px;
}

span {
    font-weight: 900;
    color: #00FF95;
}

@media (max-width: 1400px) {
   .pix-card {
    width: 100%;
   }

   .text-container{
    width: 50%;
   }
 
}

</style>