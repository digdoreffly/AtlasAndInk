<template>
  <div>
<section class="hero-section text-center text-lg-start d-flex align-items-center py-5">
  <div class="container">
    <div class="row align-items-center">
      
      <div class="col-lg-6">
        <h1 class="fw-bold mb-3">
          Documenting the <span class="text-primary">World</span><br />
          One Journey at a Time ✈️
        </h1>
        <h4 id="iddoc">
          Discover new destinations, cultures, and unforgettable adventures.
        </h4>
        <div class="d-flex gap-3 mt-4">
          <a href="explore" class="btn btn-warning fw-bold px-4">
            <i class="bi bi-globe-americas me-2"></i> Explore Now
          </a>

        </div>

        <div class="d-flex gap-4 mt-5 text-primary fs-3">
          <i class="bi bi-airplane-fill"></i>
          <i class="bi bi-geo-alt-fill"></i>
          <i class="bi bi-sun-fill"></i>
          <i class="bi bi-buildings"></i>
          <i class="bi bi-compass-fill"></i>
        </div>
      </div>


    </div>
  </div>
</section>
    <section class="py-5 text-center">
      <h3 class="fw-bold mb-4">What We Offer</h3>
      <div class="container">
        <div class="row g-4">
          <div class="col-md-4">
            <div class="card h-100 border shadow-sm p-3">
              <div class="mb-3 fs-2">🌍</div>
              <h5>Global Snapshots</h5>
              <p class="text-muted">
                Key details about every recognised country, always updated!
              </p>
            </div>
          </div>
          <div class="col-md-4">
            <div class="card h-100 border shadow-sm p-3">
              <div class="mb-3 fs-2">✈️</div>
              <h5>Plan Your Adventure</h5>
              <p class="text-muted">
                Insights that help you prepare or inspire your next trip.
              </p>
            </div>
          </div>
          <div class="col-md-4">
            <div class="card h-100 border shadow-sm p-3">
              <div class="mb-3 fs-2">🎭</div>
              <h5>Discover Cultures</h5>
              <p class="text-muted">
                From languages to customs, learn what makes each place unique.
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="py-5 text-center bg-light">
      <div class="container">
        <h4 class="fw-bold mb-3">Our Mission</h4>
        <p class="text-muted">
          At <span class="text-primary">Atlas & Ink</span>, we believe the world is best understood one country at a time.<br />
          Our mission is to bring you reliable information, stunning visuals, and fascinating cultural facts whether you’re a traveler, student, or just curious about the world.
        </p>
      </div>
    </section>

    <section class="py-5 text-center">
      <h4 class="fw-bold mb-3">Our Testimonials</h4>
      <div class="container">
        <div class="p-5 bg-secondary text-white rounded">
          Placeholder for testimonials
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
</script>

<style scoped>
.hero-section {
  background: linear-gradient(135deg, #7b2ff7, #f107a3);
  color: white;
  min-height: 80vh;
}
.hero-section h1 {
  color: white;
}

#iddoc{
  color:white;
}

.hero-section {
  background: linear-gradient(135deg, #7b2ff7 0%, #fff 100%);
  min-height: 80vh;
}
</style>