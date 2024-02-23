<template>
    <div>
      <hr />
      <div class="min-h-screen flex justify-center bg-gray-800">
        <div class="flex flex-col items-center">
          <div>
            <h1 class="text-4xl font-bold p-4 text-white">Products</h1>
          </div>
          <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-5 gap-6">
            <div v-for="item in products" :key="item.id">
              <div class="relative">
                <nuxt-link
                  :to="`/products/${item.id}`"
                  class="block w-full h-full bg-white rounded-lg overflow-hidden shadow-lg transform hover:scale-105 transition-transform duration-300"
                >
                  <img
                    class="w-full h-48 sm:h-64 lg:h-96 object-cover object-center rounded-t-lg"
                    :src="item.image"
                    :alt="item.title"
                  />
                  <div class="p-4">
                    <h1 class="text-xl font-bold mb-2 text-green-900">{{ item.title }}</h1>
                    <p class="text-gray-600">Price: $ {{ item.price }}</p>
                  </div>
                </nuxt-link>
                <button @click="addToCart(item)" class="absolute bottom-0 left-0 right-0 bg-blue-500 text-white px-4 py-2 rounded-b-md">
                    Price: $ {{ item.price }} | Add to Cart
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
   
  
<script setup>
const cart=useCart()
    useHead({
        title:"Products",
    });
    definePageMeta({
        middleware:["auth"]
    })
    const {  data: items } = await useFetch('https://fakestoreapi.com/products')
    const products=items.value
    function addToCart(item){
        console.log(item)
        cart.value.push({id:item.id,title:item.title,image:item.image,price:item.price})
    }
</script>