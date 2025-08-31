<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-white shadow-sm">
    <div class="container">
      <!-- Logo -->
      <a class="navbar-brand fw-bold text-primary" href="#">
        Atlas & Ink
      </a>

      <!-- Toggler (mobile) -->
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarNav"
        aria-controls="navbarNav"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <!-- Menu -->
      <div class="collapse navbar-collapse justify-content-end" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item">
            <a class="nav-link fw-semibold" :class="{ active: currentRoute === '/' }" href="/">
              Home
            </a>
          </li>
          <li class="nav-item">
            <a class="nav-link fw-semibold" :class="{ active: currentRoute === '/explore' }" href="/explore">
              Explore
            </a>
          </li>
          <li class="nav-item">
            <a class="nav-link fw-semibold" :class="{ active: currentRoute === '/about' }" href="/about">
              About Us
            </a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { useRoute } from "vue-router";

const route = useRoute();
const currentRoute = route.path;
</script>

<style scoped>
.nav-link {
  margin-left: 1rem;
  color: #444 !important;
  transition: 0.2s;
}
.nav-link:hover {
  color: #7b2ff7 !important;
}
.nav-link.active {
  color: #7b2ff7 !important;
  font-weight: bold;
}
</style>
