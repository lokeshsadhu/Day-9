<template>
<div class="min-h-screen flex justify-center bg-gradient-to-t from-gray-800 to-white-900">
    <div class="text-center mt-10">
    <h1 class="text-4xl font-extrabold mb-4">About Cars</h1>
    <p class="text-lg mb-8">
        Welcome to our world of automotive passion! Explore the latest and greatest in the world of cars.
    </p>
    <div class="flex items-center justify-center mb-10"><img src="/images/porsche.jpg" alt="Cars" class="car rounded-lg"></div>
    <p class="text-lg">
        Whether you're a car enthusiast or just curious about the automotive world, our about page is here to provide you with fascinating insights and information.
    </p>
    </div>
</div>
</template>

<script setup>
definePageMeta({
    middleware:["auth"]
})
</script>

<style>
.car{
    height: 300px;
    width: 560px;
}
</style>