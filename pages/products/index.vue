<template>
<div>
  <div class="flex justify-center min-h-screen bg-cover bg-center" :style="{ backgroundImage: `url(${backgroundImageUrl})` }">
    <div class="flex flex-col items-center">

      <div>
        <h1 class="text-4xl font-bold p-4 text-black">Products</h1>
      </div>

      <div class="flex flex-row">
        <div class="relative w-30 h-11 mb-4 flex items-center justify-start">
          <input
            v-model="search"
            type="text"
            placeholder="Search..."
            class="w-full h-10 px-4 text-black placeholder-gray-400 bg-opacity-50 bg-white border border-green-700 ml-2 rounded-md focus:outline-none focus:ring focus:border-green-300"
          />
        </div>

        <div class="ml-3">
          <select v-model="category" class="block appearance-none h-11 w-full bg-green-500 border border-black text-black py-3 px-4 pr-8 rounded-lg leading-tight focus:outline-black focus:bg-green-400 focus:border-green-600">
            <option selected value="">All</option>
            <option value="men's clothing">men's clothing</option>
            <option value="women's clothing">women's clothing</option>
            <option value="jewelery">jewelery</option>
            <option value="electronics">electronics</option>
          </select>
        </div>
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
const category=ref('')
const search=ref('')
const backgroundImageUrl='/images/background.jpg'
const cart=useCart()
const selectedValue=ref('All')
const toggleDropdown = () => {
  isDropdownOpen.value = !isDropdownOpen.value;
};
useHead({
    title:"Products",
});
definePageMeta({
    middleware:["auth"]
})
const {  data: items } = await useFetch('https://fakestoreapi.com/products')
const products=items.value
function addToCart(item){
    const existingProduct = cart.value.find(product => product.id === item.id);

    if (existingProduct) {
      existingProduct.quantity += 1;
    } else {
      cart.value.push({id:item.id,title:item.title,image:item.image,price:item.price,quantity:1});
    }
}

let shoppingItems=computed((event)=>{
  if(category.value==="All"){
    return products.filter((item)=>item.title.toLowerCase().includes(search.value.toLowerCase()))
  }else{
    return products.filter((item)=>item.title.toLowerCase().includes(search.value.toLowerCase()) && item.category.includes(category.value))
  }
  console.log(category.value)
  
})
</script>

