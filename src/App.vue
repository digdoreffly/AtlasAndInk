<template>
  <div id="app">
    <Navbar />

    <main class="container mt-4">
      <router-view />
    </main>

    <Footer />
  </div>
</template>

<script>
import Navbar from './components/navbar.vue'
import Footer from './components/footer.vue'

export default {
  components: { Navbar, Footer }
}
</script>
