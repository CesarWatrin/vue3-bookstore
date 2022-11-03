<script setup>
  import Book from '../components/Book.vue';
  import { bookstore } from "../assets/js/bookstore";
  import { computed, reactive } from "vue";
  import { useRoute, useRouter } from 'vue-router';

  const books = reactive(bookstore);

  const paginateBooks = computed(() => {
    return books.slice(0,8);
  });

  const route = useRoute();
  const router = useRouter();

  const handlePagination = (page) => {
    
  }
</script>
<template>
    <div class="tm-main-content">
      <section class="tm-margin-b-l">
        <header>
          <h2 class="tm-main-title">Welcome to our bookstore</h2>
        </header>
        <p>
          Shelf HTML template is provided by Tooplate. Please tell your friends about it. Thank you. Images are from
          Unsplash website. In tincidunt metus sed justo tincidunt sollicitudin. Curabitur magna tellus, condimentum
          vitae consectetur id, elementum sit amet erat.
        </p>
        <div class="tm-gallery">
          <div class="row">
              <Book v-for="book in paginateBooks" :key="book.id" :book="book" />
          </div>
        </div>
        <nav class="tm-gallery-nav">
          <ul class="nav justify-content-center">
            <li v-for="i in 4" class="nav-item pointer" @click="handlePagination(i)"><span class="nav-link">{{ i }}</span></li>
          </ul>
        </nav>
      </section>
    </div>
</template>