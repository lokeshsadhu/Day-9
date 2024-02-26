<template>
    <div class="flex items-center justify-center min-h-screen bg-cover bg-center" :style="{ backgroundImage: `url(${backgroundImageUrl})` }">
      <div class="relative w-full max-w-md bg-white backdrop-filter backdrop-blur-md bg-opacity-50 p-8 rounded-md shadow-lg">
  
        <div class="grid grid-cols-1 md:grid-cols-1 gap-4">
          <div>
            <img :src="item.image" :alt="item.title" class="w-full h-96 object-cover rounded-lg shadow-lg">
          </div>
          <div class="text-black">
            <h1 class="text-4xl font-extrabold mb-4">{{ item.title }}</h1>
            <div class="mb-4">
              <p>{{ item.description }}</p>
              <p class="font-extrabold">{{ item.rating.rate }} - ({{ item.rating.count }})</p>
              <p class="font-extrabold text-4xl">$ {{ item.price }}</p>
            </div>
            <button @click="addToCart()" class="bg-green-700 text-black py-2 px-4 rounded-lg hover:bg-lightgreen-dark focus:outline-none focus:shadow-outline-lightgreen active:bg-lightgreen-darker">
              <span v-if="inCart()">Remove from Cart</span>
              <span v-else>Add to Cart</span>
            </button>
          </div>
        </div>
  
      </div>
    </div>
  </template>
  
<script setup>
const {id}=useRoute().params
const uri='https://fakestoreapi.com/products/'+id
const {data:product}=await useFetch(uri,{key:id})
const item=product.value
const backgroundImageUrl='/images/background.jpg'
useHead({
    title:`${id}`
})

const cart=useCart()
const found=ref(false)
function inCart(){
    return !!cart.value.find((item)=>item.id===id)
}

function addToCart(){
    if(!inCart()){
        cart.value.push({id:id,title:item.title,image:item.image,price:item.price,quantity:1})
    }
    else{
        cart.value=cart.value.filter((item)=>item.id!==id)
    }
}
</script>