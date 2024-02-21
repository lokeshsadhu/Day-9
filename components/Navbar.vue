<template>
    <div>
        <nav class="bg-gray-800 p-4">
        <div class="container mx-auto flex justify-between items-center">
        <div class="flex items-center">
            <img class="image h-10 w-10 mr-2" src="https://cp.drunomics.com/files/styles/bounding_box_1600x1000/public/2022-12/icon-green-square.png?itok=9VmSTOtM" alt="Logo">
        </div>
        <div>
            <ul class="flex space-x-4">
            <li><NuxtLink to="/" class="text-white hover:text-gray-300">Home</NuxtLink></li>
            <li><NuxtLink to="/garage" class="text-white hover:text-gray-300">Garage</NuxtLink></li>
            <li><NuxtLink to="/about" class="text-white hover:text-gray-300">About</NuxtLink></li>
            <li><NuxtLink to="/account" class="text-white hover:text-gray-300">Account</NuxtLink></li>
            <li><NuxtLink to="/register" class="text-yellow-500 hover:text-gray-300">Register</NuxtLink></li>
            <li><NuxtLink to="/login" class="text-blue-300 hover:text-gray-300">Login</NuxtLink></li>
            <li><NuxtLink to="/cart" class="text-orange-500 hover:text-gray-300">Cart({{cart.length}})</NuxtLink></li>
            </ul>
        </div>
        </div>
        </nav>
    </div>
</template>

<script setup>
const cart=useCart()
console.log(cart.value.length)
</script>