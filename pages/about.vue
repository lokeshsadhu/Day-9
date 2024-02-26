<template>
<div class="relative min-h-screen bg-cover bg-center" :style="{ backgroundImage: `url(${backgroundImageUrl})` }">
    <div class="absolute inset-0 backdrop-filter backdrop-blur-md bg-opacity-50 p-8">
      <h1 class="text-3xl font-bold mb-6 text-gray-800">Welcome to <span class="text-blue-500">Mantra</span>!</h1>

      <p class="text-black-900 mb-8">
        At <span class="text-blue-500">Mantra</span>, we are passionate about fashion and committed to providing you with the best shopping experience for trendy and stylish clothing.
      </p>

      <section class="mb-8">
        <h2 class="text-2xl font-bold mb-4 text-gray-800">Our Mission</h2>
        <p class="text-black-900">
          Our mission is to empower you to express your unique style through high-quality, affordable fashion. We curate a diverse collection of clothing that caters to different tastes, occasions, and sizes.
        </p>
      </section>

      <section class="mb-8">
        <h2 class="text-2xl font-bold mb-4 text-gray-800">Quality and Sustainability</h2>
        <p class="ttext-black-900">
          We believe in quality and sustainability. Our clothing is crafted with care, using eco-friendly materials whenever possible. We strive to make fashion choices that are not only stylish but also contribute to a more sustainable and ethical industry.
        </p>
      </section>

      <section class="mb-8">
        <h2 class="text-2xl font-bold mb-4 text-gray-800">Explore Our Collections</h2>
        <p class="text-black-900">
          Dive into our collections and discover the latest trends, timeless classics, and everything in between. From casual wear to elegant dresses, we've got something for every style preference.
        </p>
      </section>

      <section class="mb-8">
        <h2 class="text-2xl font-bold mb-4 text-gray-800">Easy and Secure Shopping</h2>
        <p class="text-black-900">
          Shopping with us is easy, secure, and convenient. Browse our online store from the comfort of your home, explore detailed product descriptions, and enjoy a seamless checkout process. We prioritize the security of your information to ensure a worry-free shopping experience.
        </p>
      </section>

      <section class="mb-8">
        <h2 class="text-2xl font-bold mb-4 text-gray-800">Customer Satisfaction</h2>
        <p class="text-black-900">
          Your satisfaction is our top priority. Our customer support team is here to assist you with any questions or concerns. We value your feedback and continuously strive to improve our services.
        </p>
      </section>

      <section class="mb-8">
        <h2 class="text-2xl font-bold mb-4 text-gray-800">Stay Connected</h2>
        <p class="text-black-900">
          Join our community! Follow us on social media for the latest updates, style inspiration, and exclusive promotions. Subscribe to our newsletter to receive special offers directly to your inbox.
        </p>
      </section>

      <p class="text-black-900">
        Thank you for choosing <span class="text-blue-500">Mantra</span> for your fashion needs. Happy shopping!
      </p>
    </div>
  </div>
<!-- <ContentDoc path="/"/> -->
</template>

<script setup>
definePageMeta({
    middleware:["auth"]
})
useHead({
    title:"About Page"
})
const backgroundImageUrl='/images/background.jpg'
</script>

<style>
.car{
    height: 300px;
    width: 560px;
}
</style>