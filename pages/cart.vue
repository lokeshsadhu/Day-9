<template>
  <div class="flex items-center justify-center min-h-screen bg-cover bg-center" :style="{ backgroundImage: `url(${backgroundImageUrl})` }">
    <div class="backdrop-blur-md bg-opacity-50 bg-gray-400 text-black p-8 rounded-md">
      <h1 class="text-3xl text-center text-black font-extrabold mb-6 mt-5">Shopping Cart</h1>

      <div v-if="cart.length === 0" class="flex flex-col items-center justify-center">
        <p>Your cart is empty.</p>
        <button @click="products" class="border-2 mt-5 border-black text-black px-4 py-2 bg-white hover:text-white rounded-lg hover:bg-black transition-all duration-300">
            Shop Products
        </button>
      </div>
      

      <div v-else>
        <div v-for="(item, index) in cart" :key="index" class="flex items-center mb-8">
          <img :src="item.image" alt="Product" class="w-36 h-48 object-cover rounded-md mr-6">
          <div>
            <h2 class="text-xl font-bold mb-2">{{ item.title }}</h2>
            <p>Quantity : <span class="text-green-900">{{ item.quantity }}</span></p>
            <p>Price : <span class="text-yellow-900 font-extrabold">{{ item.quantity*item.price }}</span></p>
            <button @click="removeItem(index)" class="text-red-500 hover:text-red-700 focus:outline-none">
              Remove
            </button>
          </div>
        </div>
        <h1 class="text-3xl text-end font-extrabold mb-6 mt-5">Total : $ {{ total }}</h1>
      </div>
    </div>
  </div>
</template>


<script setup>
const cart=useCart()
const backgroundImageUrl='/images/background.jpg'
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
  total.value+=i.price*i.quantity
}
function removeTotal(){
  total.value=0
  for(let i of cart.value){
  total.value+=(i.price*i.quantity)
  }
  console.log(total.value)
}
function products(){
  navigateTo("/products")
}
</script>