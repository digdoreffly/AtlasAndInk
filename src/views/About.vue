<template>
  <div>
    <!-- Hero Section -->
    <section class="about-hero d-flex align-items-center justify-content-center text-center">
      <div>
        <h2 class="fw-bold text-dark">ABOUT US</h2>
        <img
          src="https://i.pravatar.cc/150?img=3"
          alt="Profile"
          class="profile-img mt-3"
        />
      </div>
    </section>

    <!-- Content Section -->
    <section class="container py-5">
      <div class="row">
        <div class="col-md-6 mb-4">
          <div class="content-box p-4 shadow-sm rounded bg-light">
            <h5 class="fw-bold">Our Story</h5>
            <p>
              We started Atlas & Ink with a mission to help people discover cultures
              and explore the world with reliable information.
            </p>
          </div>
        </div>
        <div class="col-md-6 mb-4">
          <div class="content-box p-4 shadow-sm rounded bg-light">
            <h5 class="fw-bold">Our Vision</h5>
            <p>
              To inspire travelers, students, and explorers by providing cultural
              insights and essential travel tips across the globe.
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <Footer />
  </div>
</template>

<script setup>

</script>

<style scoped>
.about-hero {
  background-color: #8ee593;
  height: 250px;
  position: relative;
}
.profile-img {
  width: 120px;
  height: 120px;
  border-radius: 50%;
  border: 5px solid #fff;
  object-fit: cover;
}
.content-box {
  min-height: 200px;
}
</style>
