<template>
    <v-card class="product-detail d-flex ga-10">
        <img 
            src="/public/images/telescope.jpg" 
            class="image"
        />
        <div class="d-flex flex-column ga-3">
            <h2>Telescópio Refletor Newtoniano 130mm Uranum Equatorial Astronômico Luneta</h2>
            <div class="d-flex flex-row align-center justify-start ga-10">
                <p>Marca: Uranum</p>
                <v-rating
                    v-model="rating"
                    active-color="orange-lighten-1"
                    color="orange-lighten-1"
                    size="small"
                    density="compact"
                    readonly
                />
            </div>
            <p class="price">R$ 2.450,99</p>
            <v-divider />
            <div>
                <label for="quantity">Quantidade:</label>
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
            </div>
        </div>
    </v-card>

</template>

<script setup>
const rating = ref(4)
const quantity = ref(1)

</script>


<style scoped>
.product-detail {
    background-color: rgba(0, 0, 0, 0); 
    color: #00FF95;
    width: 50vw;
    
}

.image {
    width: 15vw;
    border-radius: 4px;
}

.input {
    background-color: #0d3121;
    margin-left: 5px;
    width: 60px;
    height: 30px;
    border-radius: 5px;
    border: none;
    padding-left: 15px;
}

.price {
    color: #bc01d4; 
    font-size: 24px;
    font-weight: 900;
}

p, label {
    color: #1f855a;
}

</style>