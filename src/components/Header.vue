<script setup>
  import { RouterLink } from 'vue-router';
</script>

<template>
  <header class="tm-site-header">
    <h1 class="tm-site-name">Shelf</h1>
    <p class="tm-site-description">Your Online Bookstore</p>

    <nav class="navbar navbar-expand-md tm-main-nav-container">
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#tmMainNav" aria-controls="tmMainNav" aria-expanded="false" aria-label="Toggle navigation">
        <i class="fa fa-bars"></i>
      </button>

      <div class="collapse navbar-collapse tm-main-nav" id="tmMainNav">
        <ul class="nav nav-fill tm-main-nav-ul">
          <li class="nav-item">
            <RouterLink class="nav-link" :to="{ name: 'home' }">Home</RouterLink>
          </li>
          <li class="nav-item">
            <RouterLink class="nav-link" :to="{ name: 'about' }">About</RouterLink>
          </li>
        </ul>
      </div>
    </nav>

  </header>
</template>