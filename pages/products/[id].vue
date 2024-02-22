<template>
    <div class="min-h-screen flex justify-center bg-gradient-to-t from-gray-800 to-white-900">
      <div class="text-center text-black mt-4">
        <h1 class="text-4xl font-extrabold mb-4">{{ item.title }}</h1>
        <img :src="item.image" :alt="item.title" class="w-full h-96 object-cover mb-4 rounded-lg">
        <button @click="addToCart()" class="bg-green-700 text-white py-2 px-4 rounded-lg hover:bg-lightgreen-dark focus:outline-none focus:shadow-outline-lightgreen active:bg-lightgreen-darker">
            <span v-if="inCart()">Remove from Cart</span>
            <span v-else>Add to Cart</span>
        </button>
        
      </div>
    </div>
</template>

<script setup>
const {id}=useRoute().params
const uri='https://fakestoreapi.com/products/'+id
const {data:product}=await useFetch(uri,{key:id})
const item=product.value
// const route=useRoute()
// const name=computed(()=>{
//     return route.params.name.replace('-',' ')
// })

useHead({
    title:`${id}`
})

// const fullName=computed(()=>{
//     return `${route.params.title}`
// })

const cart=useCart()
const found=ref(false)
function inCart(){
    return !!cart.value.find((item)=>item.id===id)
}

function addToCart(){
    if(!inCart()){
        cart.value.push({id:id,title:item.title,image:item.image})
    }
    else{
        cart.value=cart.value.filter((item)=>item.id!==id)
    }
}
</script>