<script setup>
  import { defineProps } from 'vue';
  const props = defineProps({
    book: Object,
  });
</script>
<template>
  <figure class="col-lg-3 col-md-4 col-sm-6 col-12 tm-gallery-item">
    <RouterLink to="">
      <div class="tm-gallery-item-overlay">
        <img :src="'../src/assets/img/' + book.cover" alt="Image" class="img-fluid tm-img-center">
      </div>
      <p class="tm-figcaption">{{ book.title }} <br> <small>{{ book.author }}</small></p>
    </RouterLink>
  </figure>
</template>