<template>
    <app-header />
    <main class="d-flex flex-column align-center">
        <div class="d-flex ga-10 mt-16">
            <div>
                <app-product />
                <h1 class="my-8">Finalizando compra</h1>
                <app-user-data-form />
                <app-adress-form />
                <app-payment-form />
            </div>
            <app-summary
                :quantity=1 
                :price="product.price"
                :rating="product.rating"
                :freightCharges="product.freightCharges"
            />
            
        </div>
    </main>
</template>

<script setup>
    const product = {
        id: 1,
        price: 2450.99,
        name: 'Telescópio Refletor Newtoniano 130mm Uranum Equatorial Astronômico Luneta',
        rating: 4,
        brand: 'Uranum',
        freightCharges: 30
    }   
    
</script>

<style scoped>
main {
    color: #00FF95;
}
</style>