<template>

    <div>
        <input type="text" />
        <h3 class="mb-5">Contato</h3>
        <div class="d-flex ga-3">
            <v-text-field 
                label="Nome completo*" 
                :rules="[requiredRule]"
                @update:model-value="emitInput('name', $event)"

            />
            <v-text-field 
                label="Telefone*" 
                :rules="[requiredRule]" 
                @update:model-value="emitInput('phone', $event)"
            />
        </div>
        <v-text-field 
            label="E-mail" 
            @update:model-value="emitInput('email', $event)"
            />
    </div>

</template>

<script setup>

    const requiredRule = inputValue => !!inputValue || 'Este campo é obrigatório'

    const emit = defineEmits(['updateUserData'])

    const emitInput = (field, value) => {
        emit('updateUserData', { field, value })
    }

</script>