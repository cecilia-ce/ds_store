<template>
<app-header />
<main class="d-flex flex-column align-center">

    <div class="w-25 mt-10">
        <h1>Sua compra foi realizada com sucesso!</h1>
    </div>

    <div class="d-flex flex-row align-center justify-center ga-5 mt-10">
        <img 
            src="/public/images/successImg.png"
            alt="figura ilustrativa de robô com um carrinho de compras" 
            class="w-25"
        />
        <app-buy-details :buy-details="buyDetails" />
    </div>

</main>
</template>

<script setup>
const props = defineProps(['buyDetails'])

</script>

<style scoped>
    .header {
        box-shadow: 0 2px 25px -10px #00FF95;
        color:#00FF95;
    }

    .background-container {
        position: relative;
        background-color: none;
    }

    main {
        color: #00FF95;
    }

    h1 {
        text-align: center;
    }
</style>