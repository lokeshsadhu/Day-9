<template>
    <div class="flex items-center justify-center min-h-screen bg-cover bg-center" :style="{ backgroundImage: `url(${backgroundImageUrl})` }">
        <div class="relative w-full max-w-md bg-white backdrop-filter backdrop-blur-md bg-opacity-50 p-8 rounded-md shadow-lg">
        <h1 class="text-2xl font-semibold mb-4">Change Password</h1>
        <form @submit.prevent="login">
            <div class="mb-4">
            <label for="oldPassword" class="block text-sm font-medium text-black-900">Old Password:</label>
            <input v-model="oldPassword" type="text" id="oldPassword" class="mt-1 p-2 w-full border rounded-md" required />
            </div>
            <div class="mb-4">
            <label for="newPassword" class="block text-sm font-medium text-black-900">New Password:</label>
            <input v-model="newPassword" type="password" id="newPassword" class="mt-1 p-2 w-full border rounded-md" required />
            </div>
            <button @click="change" type="submit" class="w-full bg-blue-500 text-white p-2 rounded-md">Change Password</button>
        </form>
        <p class="mt-4 text-center text-green-600" v-show="changed">Password Changed</p>
        </div>
    </div>
</template>
<script setup>
const backgroundImageUrl='/images/background.jpg'
const users=usersList()
const oldPassword=ref('')
const newPassword=ref('')
const changed=ref(false)
console.log(users.value)
function change(){
  if(users.value[0].pass===oldPassword.value){
    users.value[0].pass=newPassword.value
    changed.value=true
  }
}
</script>