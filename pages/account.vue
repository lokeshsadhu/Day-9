<template>
  <div class="flex items-center justify-center min-h-screen bg-cover bg-center" :style="{ backgroundImage: `url(${backgroundImageUrl})` }">
    <div class="relative w-full max-w-md bg-white backdrop-filter backdrop-blur-md bg-opacity-50 p-8 rounded-md shadow-lg">
      <h1 class="text-3xl font-extrabold mb-6 text-black">My Account</h1>

      <div class="flex items-center mb-8">
        <div>
          <h2 class="text-xl font-semibold">Hi! Lokesh</h2>
          <p class="text-black">Welcome to your account dashboard!</p>
        </div>
      </div>

      <div class="mb-8">
        <h2 class="text-2xl font-bold mb-4">Dashboard</h2>
        <p class="text-black">View your recent activity, orders, and more.</p>
      </div>

      <div>
        <h2 class="text-2xl font-bold mb-4">Settings</h2>
        <p class="text-black">Update your profile, password, and notification preferences.</p>
      </div>

      <div class="text-center mt-10">
        <button @click="logout" class="bg-red-600 hover:bg-red-500 text-white font-bold py-2 px-4 rounded">
          Logout
        </button>
        <button @click="changePassword" class="bg-yellow-600 hover:bg-red-500 text-white font-bold ml-5 py-2 px-4 rounded">
          Change Password
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
const backgroundImageUrl='/images/suit.jpg'
definePageMeta({
    // layout:"sidebar",
    middleware:["auth"]
})
const loginStatus=isLoggedIn()
function logout(){
  loginStatus.value=false
  navigateTo('/login')
}
function changePassword(){
  navigateTo('/changePass')
}
</script>