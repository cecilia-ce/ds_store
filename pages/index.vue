<template>
     <div class="d-flex justify-space-between align-center pa-10 border-b-thin title header">
         <div class="d-flex align-center ga-5">
             <v-img width="55" src="/public/images/logo.svg" />
             <h1>Deep Space Store</h1>
         </div>
     </div>
     <main class="h-75 d-flex flex-column justify-center align-center mt-10">
          <v-card
               variant="tonal"
               class="card d-flex flex-column ma-3"
          >    
               <div class="d-flex ga-2">
                    <img class="w-25" :src="product.image" />
                    <h2>{{ product.name }}</h2>
               </div>
               <v-btn
                    @click="navigateTo(`/checkout/${product.id}`)"
                    class="button"
               >
                    Comprar
               </v-btn>
          </v-card>
     </main>
     <app-footer class="footer"/>
</template>

<script setup>

const product = {
     id: 1,
     price: 3450.99,
     name: 'Telescópio Refletor Newtoniano 130mm Uranum Equatorial Astronômico Luneta',
     rating: 4,
     brand: 'Uranum',
     freightCharges: 50,
     image: '/images/telescope.jpg'
} 
</script>

<style scoped>
.header {
    box-shadow: 0 2px 25px -10px #00FF95;
    color:#00FF95;
}

.card {
     width: 50vw;
     color: #00FF95;
}

.button {
    background-color: #bc01d4; 
}

</style>