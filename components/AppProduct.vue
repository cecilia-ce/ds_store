<template>
    <v-card class="product-detail d-flex ga-10">
        <img 
            src="/public/images/telescope.jpg" 
            class="image"
        />
        <div class="d-flex flex-column ga-3">
            <h2>{{ name }}</h2>
            <div class="d-flex flex-row align-center justify-start ga-10">
                <p>Marca: {{ brand }}</p>
                <v-rating
                    v-model="ratingValue"
                    active-color="orange-lighten-1"
                    color="orange-lighten-1"
                    size="small"
                    density="compact"
                    readonly
                />
            </div>
            <p class="price">R$ {{ price }}</p>          
        </div>
    </v-card>

</template>

<script setup>

const props = defineProps(['name', 'brand', 'rating', 'price'])

const ratingValue = ref(props.rating)

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

.price {
    color: #bc01d4; 
    font-size: 24px;
    font-weight: 900;
}

p, label {
    color: #1f855a;
}

</style>