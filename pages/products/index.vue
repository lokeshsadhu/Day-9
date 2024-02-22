<template>
    <hr/>
<div class="min-h-screen flex justify-center bg-gray-800">
    <div class="flex flex-col items-center">
    <div>
        <h1 class="text-4xl font-bold p-4 text-white">Products</h1>
    </div>
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-10 m-5">
        <div v-for="item in products" :key="item.id">
        <nuxt-link :to="`/products/${item.id}`" class="block w-full h-full bg-white rounded-lg overflow-hidden shadow-lg transform hover:scale-105 transition-transform duration-300">
            <img class="w-full h-48 sm:h-64 lg:h-96 object-cover object-center rounded-t-lg" :src="item.image" :alt="item.title">
            <div class="p-4">
            <h1 class="text-xl font-bold mb-2">{{ item.title }}</h1>
            </div>
        </nuxt-link>
        </div>
    </div>
    </div>
</div>
</template>
   
  
<script setup>
    useHead({
        title:"Products",
    });
    definePageMeta({
        middleware:["auth"]
    })
    const {  data: items } = await useFetch('https://fakestoreapi.com/products')
    const products=items.value
</script>