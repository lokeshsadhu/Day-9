<template>
    <div class="bg-gradient-to-t from-gray-800 to-white-900 min-h-screen flex justify-center">
        <div class="mt-10">
        <h1 class="text-2xl font-semibold mb-4">Register</h1>
        <form @submit.prevent="login">
            <div class="mb-4">
            <label for="username" class="block text-sm font-medium text-gray-600">Username:</label>
            <input v-model="username" type="text" id="username" class="mt-1 p-2 w-full border rounded-md" required />
            </div>
            <div class="mb-4">
            <label for="password" class="block text-sm font-medium text-gray-600">Password:</label>
            <input v-model="password" type="password" id="password" class="mt-1 p-2 w-full border rounded-md" required />
            </div>
            <button @click="reg(username, password)" type="submit" class="w-full bg-blue-500 text-white p-2 rounded-md">Register</button>
        </form>
        </div>
    </div>
</template>

<script setup>
const users=usersList()
const {$register}=useNuxtApp()
const username=ref('')
const password=ref('')
const registered=ref(false)
function reg(){
    let a=$register(username.value,password.value)
    console.log(users.value)
    registered.value=true
    if(registered.value===true){
        navigateTo({path:'/login'})
    }
    registered.value=false
}
</script>