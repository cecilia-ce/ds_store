<template>
    <div class="card">

        <input type="text" />

        <h3 class="mb-5">Endereço para entrega</h3>

        <div class="d-flex ga-3">
            <v-text-field 
                label="CEP*"
                v-model="adressForm.cep"
                @blur="fetchAddressData"
            />
            <v-text-field 
                label="Endereço*" 
                v-model="adressForm.street"
            />
        </div>

        <div class="d-flex ga-3">
            <v-text-field 
                label="Número"
                v-model="adressForm.number"
                class="textfield-number"
            />
            <v-text-field 
                label="Bairro*" 
                v-model="adressForm.neighborhood"
            />
            <v-text-field 
                label="Complemento"
                v-model="adressForm.complement"
            />
            <v-text-field 
            label="Cidade/UF" 
            v-model="cityUf"
            />
        </div>

    </div>
</template>


<script setup>


const adressForm = ref({
    cep: null,
    street: null,
    neighborhood: null,
    number: null,
    complement: null,
    city: null,
    fu: null
})

const emit = defineEmits(['updateAdress'])

const cityUf = computed(() => {
  if (adressForm.value.city) {
    return `${adressForm.value.city}/${adressForm.value.fu}`
  } else {
    return ''
  }
})

async function fetchAddressData() {
    try {
        const response = await fetch(`https://viacep.com.br/ws/${adressForm.value.cep}/json/`)
        const data = await response.json()
        adressForm.value = {
            ...adressForm.value,
            street: data.logradouro,
            neighborhood: data.bairro,
            number: '',
            complement: '',
            city: data.localidade,
            fu: data.uf
        }
        emit('updateAdress', { adressForm })
    }catch(error){
        console.log(error)
    }
} 
</script>
