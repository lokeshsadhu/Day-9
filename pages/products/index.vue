<template>
<div>
  <div class="flex items-center justify-center min-h-screen bg-cover bg-center" :style="{ backgroundImage: `url(${backgroundImageUrl})` }">
    <div class="flex flex-col items-center">

      <div>
        <h1 class="text-4xl font-bold p-4 text-black">Products</h1>
      </div>

      <div class="relative w-full mb-4 flex items-center justify-start">
        <input
          v-model="search"
          type="text"
          placeholder="Search..."
          class="w-full h-10 px-4 text-black placeholder-gray-400 bg-opacity-50 bg-white border border-green-700 ml-2 rounded-md focus:outline-none focus:ring focus:border-green-300"
        />
      </div>
              
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-5 gap-6">
        <div v-for="item in shoppingItems" :key="item.id" class="relative group">
          <nuxt-link
            :to="`/products/${item.id}`"
            class="block w-full h-full bg-white rounded-lg overflow-hidden shadow-lg transform hover:scale-105 transition-transform duration-300"
          >
            <img
              class="h-48 object-cover object-center rounded-t-lg"
              :src="item.image"
              :alt="item.title"
            />
            <div class="p-4 text-center">
              <h1 class="text-xl font-bold mb-2 text-green-900">{{ item.title }}</h1>
              <br/>
            </div>
          </nuxt-link>
          <button @click="addToCart(item)" class="absolute bottom-0 left-0 right-0 bg-green-500 text-black py-2 px-4 rounded-b-md group-hover:opacity-100 transition-opacity duration-300">
            Price : $ {{item.price}} | Add to Cart
          </button>
        </div>
      </div>
    </div>
  </div>
</div>
</template>

<script setup>
const search=ref('')
const backgroundImageUrl='/images/background.jpg'
const cart=useCart()
useHead({
    title:"Products",
});
definePageMeta({
    middleware:["auth"]
})
const {  data: items } = await useFetch('https://fakestoreapi.com/products')
let products=items.value
function addToCart(item){
    const existingProduct = cart.value.find(product => product.id === item.id);

    if (existingProduct) {
      existingProduct.quantity += 1;
    } else {
      cart.value.push({id:item.id,title:item.title,image:item.image,price:item.price,quantity:1});
    }
}

const shoppingItems=computed(()=>{
return products.filter((item)=>item.title.toLowerCase().includes(search.value.toLowerCase()))
console.log(products)
})
</script>

