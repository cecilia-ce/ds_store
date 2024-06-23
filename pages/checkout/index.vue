<template>
    <app-header />

    <main class="d-flex flex-column align-center">
        <div class="d-flex ga-10 mt-16">
            <div>
                <app-product 
                    :name="product.name"
                    :brand="product.brand"
                    :rating="product.rating"
                    :price="product.price"
                />
                <h1 class="my-8">Finalizando compra</h1>
                <app-user-data-form 
                    @updateUserData="updateUserData"
                />
                <app-adress-form />
                <app-payment-form />
            </div>
            <app-summary
                :price="product.price"
                :freightCharges="product.freightCharges"
            />
        </div>
    </main>

    <v-footer class="d-flex flex-column pa-10 mt-10">
        <p>Desenvolvido por Cecília Albuquerque</p> 
        <p>2024</p>
    </v-footer>
</template>

<script setup>

    const product = {
        id: 2,
        price: 3450.99,
        name: 'Telescópio Refletor Newtoniano 130mm Uranum Equatorial Astronômico Luneta',
        rating: 4,
        brand: 'Uranum',
        freightCharges: 50
    }   

    const user = ref({
        name: null,
        phone: null,
        email: null
    })

    const updateUserData = ({ field, value }) => {
        user.value[field] = value
        console.log(user.value)
    }
    
</script>

<style scoped>

    main {
        color: #00FF95;
    }

</style>