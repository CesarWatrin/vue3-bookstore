<script setup>
  import Book from '../components/Book.vue';
  import { bookstore } from "../assets/js/bookstore";
  import {computed, ref, reactive, watch, onMounted} from "vue";
  import { useRoute, useRouter } from 'vue-router';

  const books = reactive(bookstore);
  const route = useRoute();
  const router = useRouter();
  const MAX_BOOKS = 4;
  const indexStart = ref(0);
  const indexEnd = ref(MAX_BOOKS)

  const refreshBookList = () => {
    let {page} = route.query;

    if (typeof page === 'undefined') {
      page = 1;
    }

    indexStart.value = (page - 1) * MAX_BOOKS;
    indexEnd.value = MAX_BOOKS * page;
  };

  const paginateBooks = computed(() => {
    return books.slice(indexStart.value, indexEnd.value);
  });

  const handlePagination = (page) => {
    router.push({
      query: {
        page
      },
    });
  };

  const countPages = computed(() => {
    return Math.ceil(books.length/MAX_BOOKS);
  });

  watch(
      () => route,
      (newValue, oldValue) => { refreshBookList(); },
      { deep: true, immediate: true }
  );
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
            <li v-for="i in countPages" class="nav-item" @click="handlePagination(i)">
              <span
                  :class="{ active: (route.query.page === i.toString()) || (i === 1 && !route.query.page) }"
                  class="nav-link">
                {{ i }}
              </span>
            </li>
          </ul>
        </nav>
      </section>
    </div>
</template>