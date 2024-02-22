<template>
<div class="relative min-h-screen bg-cover bg-center" :style="{ backgroundImage: `url(${backgroundImageUrl})` }">
    <div class="absolute inset-0 backdrop-filter backdrop-blur-md bg-opacity-50"></div>
    <div class="relative z-10 flex justify-center items-center h-full">
    <div class="mt-10 text-black">
        <h1 class="text-2xl font-semibold mb-4">Login</h1>
        <form @submit.prevent="login">
        <div class="mb-4">
        <label for="username" class="block text-sm font-medium text-black-600">Username:</label>
        <input v-model="username" type="text" id="username" class="mt-1 p-2 w-full border rounded-md" required />
        </div>
        <div class="mb-4">
        <label for="password" class="block text-sm font-medium text-black-600">Password:</label>
        <input v-model="password" type="password" id="password" class="mt-1 p-2 w-full border rounded-md" required />
        </div>
        <button @click="log(username, password)" type="submit" class="w-full bg-blue-500 text-white p-2 rounded-md">Login</button>
        <div class="text-center mt-4">
            <p>For Login you need to register First!</p>
            <p @click="register" class="hover:text-blue-500 cursor-pointer">Want to register? Click here!</p>
        </div>
        <p class="text-red-700 text-center" v-if="errorShow">Incorrect Credentials</p>
        </form>
    </div>
    </div>
</div>
</template>

<script setup>
import { useSSRContext } from 'vue';
const backgroundImageUrl='/images/suit.jpg'
const {login}=useNuxtApp()
const users=usersList()
const username=ref('')
const password=ref('')
const loginStatus=isLoggedIn()
const errorShow=ref(false)
function log(username,password){
    let a=login(username,password)
    console.log(a)
    if(a){
        loginStatus.value=true
        if(loginStatus){
            navigateTo('/')
        }
    }else{
        errorShow.value=true
    }
    
}
function register(){
    navigateTo('/register')
}
useHead({
    title:"Login Page"
})
definePageMeta({
    middleware:["auth"]
})
</script>