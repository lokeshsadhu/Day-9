<template>
<div class="bg-cover bg-center min-h-screen flex items-center justify-center" :style="{ backgroundImage: `url(${backgroundImageUrl})` }">
    <div class="text-center">
        <div>
            <h1 class="text-7xl font-extrabold mb-4 text-black mt-10">Welcome!</h1>
            <p class="text-5xl text-black mb-5">Explore the collection of Fashion.</p>
        </div>
    </div>
</div>
</template>
    
<script setup>
import { useSSRContext } from 'vue';

const {login}=useNuxtApp()
const users=usersList()
const username=ref('')
const password=ref('')

const backgroundImageUrl= '/images/background.jpg'
definePageMeta({
    middleware:["auth"]
})
</script>