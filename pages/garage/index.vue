<template>
   <div class="min-h-screen flex justify-center bg-gradient-to-t from-gray-800 to-#18181b-900">
    <div class="flex flex-col items-center">
    <div>
        <h1 class="text-4xl font-bold p-4">My Garage</h1>
    </div>
    
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4">

        <nuxt-link to="/garage/car-porsche" class="bg-white rounded-lg overflow-hidden shadow-lg">
            <img class="w-full h-48 object-cover object-center" src="/images/porsche.jpg" alt="Porsche">
            <div class="p-4">
                <h1 class="text-xl font-bold mb-2">Porsche</h1>
            </div>
        </nuxt-link>

        <nuxt-link to="/garage/car-bmw" class="bg-white rounded-lg overflow-hidden shadow-lg">
            <img class="w-full h-48 object-cover object-center" src="/images/bmw.jpg" alt="BMW">
            <div class="p-4">
                <h1 class="text-xl font-bold mb-2">BMW</h1>
            </div>
        </nuxt-link>

        <nuxt-link to="/garage/car-bmw" class="bg-white rounded-lg overflow-hidden shadow-lg">
            <img class="w-full h-48 object-cover object-center" src="/images/mercedes.jpg" alt="Mercedes">
            <div class="p-4">
                <h1 class="text-xl font-bold mb-2">Mercedes</h1>
            </div>
        </nuxt-link>
        </div>
    </div>
   </div>
</template>

<script setup>
    useHead({
        title:"My Garage",
    });
    definePageMeta({
        middleware:["auth"]
    })
</script>