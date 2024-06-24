<template>
    <app-header />

    <main class="d-flex flex-column align-center">
        <div class="container">
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
                <app-adress-form 
                    @updateAdress="updateAdress"
                />
                <app-payment-form 
                    :product-value="finalPrice"
                />
            </div>
            <app-summary
                :price="product.price"
                :freightCharges="product.freightCharges"
                @updateTotalPrice="updateTotalPrice"
                @submit="navigateTo('/success')"
            />
        </div>
    </main>
    <app-footer />
</template>

<script setup>

    const product = {
        id: 1,
        price: 3450.99,
        name: 'Telescópio Refletor Newtoniano 130mm Uranum Equatorial Astronômico Luneta',
        rating: 4,
        brand: 'Uranum',
        freightCharges: 50,
        image: '/public/images/telescope.jpg'
    }   

    const user = ref({
        name: null,
        phone: null,
        email: null
    })

    const adress = ref({
        cep: null,
        street: null,
        neighborhood: null,
        number: null,
        complement: null,
        city: null,
        fu: null
    })

    const finalPrice = ref()

    const updateUserData = ({ field, value }) => {
        user.value[field] = value
    }

    const updateAdress = ( adressForm ) => {
        adress.value.city = adressForm
        console.log(adress.value)
    }

    const updateTotalPrice = ( totalPrice ) => {
        finalPrice.value = totalPrice
    }

    function buyProduct() {
        navigateTo('/success')
    }
   
</script>

<style scoped>

    main {
        color: #00FF95;
    }

    .container {
        display: flex;
        gap: 40px;
        margin-top: 64px;
    }

    @media (max-width: 1400px) {
        .container {
            display: flex;
            flex-direction: column;
            gap: 40px;
            margin-top: 64px;
        }
    }

</style>