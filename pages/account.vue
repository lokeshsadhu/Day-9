<template>
    <div class="min-h-screen flex justify-center bg-gradient-to-t from-gray-800 to-white-900">
      <div class="bg-transparent p-8">
        <h1 class="text-3xl font-extrabold mb-6 text-gray-800">My Account</h1>
  
        <div class="flex items-center mb-8">
          <div>
            <h2 class="text-xl font-semibold">Hi! Lokesh</h2>
            <p class="text-gray-600">Welcome to your account dashboard!</p>
          </div>
        </div>
  
        <div class="mb-8">
          <h2 class="text-2xl font-bold mb-4 text-gray-800">Dashboard</h2>
          <!-- Your dashboard content goes here -->
          <p class="text-gray-600">View your recent activity, orders, and more.</p>
        </div>
  
        <div>
          <h2 class="text-2xl font-bold mb-4 text-gray-800">Settings</h2>
          <!-- Your settings content goes here -->
          <p class="text-gray-600">Update your profile, password, and notification preferences.</p>
        </div>
      </div>
    </div>
</template>

<script setup>
definePageMeta({
    layout:"sidebar"
})
</script>