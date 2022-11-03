<script setup>
  import Header from '../components/Header.vue'
  import Footer from "../components/Footer.vue";
</script>

<template>
  <div class="container">
    <Header />
    <slot />
    <Footer />
  </div>
</template>