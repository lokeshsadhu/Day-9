<template>
    <div class="min-h-screen flex justify-center bg-gradient-to-t from-gray-800 to-white-900">
      <div class="bg-transparent">
        <h1 class="text-3xl text-center font-extrabold mb-6 text-gray-800 mt-5">Shopping Cart</h1>
        <div v-if="cart.length === 0" class="text-gray-600">
          Your cart is empty.
        </div>
  
        <div v-else>
          <div v-for="(item, index) in cart" :key="index" class="flex items-center mb-8">
            <img :src="item.image" alt="Product" class="w-96 h-52 object-cover rounded-md mr-6 ">
            <div>
              <h2 class="text-xl font-semibold mb-2">{{ item.title }}</h2>
              <button @click="removeItem(index)" class="text-red-500 hover:text-red-700 focus:outline-none">
                Remove
              </button>
            </div>
          </div>
        </div>
        <h1 class="text-3xl text-end font-extrabold mb-6 text-gray-800 mt-5">Total : {{ total }}</h1>
      </div>
      
    </div>
  </template>

<script setup>
const cart=useCart()

function removeItem(index) {
  console.log(index)
  console.log(cart.index)
  cart.value=cart.value.filter((item,i)=>i!==index)
  removeTotal()

}
definePageMeta({
    middleware:["auth"]
})
console.log(cart.value)
const total=ref(0)
for(let i of cart.value){
  total.value+=i.price
}
function removeTotal(){
  total.value=0
  for(let i of cart.value){
  total.value+=i.price
  }
}
</script>