<template>
    <div class="min-h-screen flex justify-center bg-gradient-to-t from-gray-800 to-white-900">
      <div class="text-center text-black mt-4">
        <h1 class="text-4xl font-extrabold mb-4">{{ name }}</h1>
        <img :src="`/images/${route.params.name}.jpg`" alt="" class="w-full h-64 object-cover mb-4 rounded-lg">
        <button @click="addToCart" class="bg-green-700 text-white py-2 px-4 rounded-lg hover:bg-lightgreen-dark focus:outline-none focus:shadow-outline-lightgreen active:bg-lightgreen-darker">
            <span v-if="inCart()">Remove from Cart</span>
            <span v-else>Add to Cart</span>
        </button>
        
      </div>
    </div>
</template>

<script setup>
const route=useRoute()
const name=computed(()=>{
    return route.params.name.replace('-',' ')
})

useHead({
    title:`Car - ${route.params.name}`
})

const fullName=computed(()=>{
    return `${route.params.name}`
})

const cart=useCart()
const found=ref(false)
function inCart(){
    return !!cart.value.find((item)=>item.name===fullName.value)
}

function addToCart(){
    if(!inCart()){
        cart.value.push({name:fullName.value})
    }
    else{
        cart.value=cart.value.filter((item)=>item.name!==fullName.value)
    }
}
console.log(fullName.value)
console.log(cart.value)
</script>