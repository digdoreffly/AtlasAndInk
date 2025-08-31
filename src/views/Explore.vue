<template>
  <div>
    <!-- Hero Section -->
    <section
      class="explore-hero text-center d-flex flex-column align-items-center justify-content-center"
    >
      <h2 class="fw-bold text-dark">Explore Countries</h2>
      <p>Browse by region or search for a specific country</p>

      <!-- Search bar -->
      <div class="search-box d-flex align-items-center mt-3">
        <input
          type="text"
          v-model="searchQuery"
          placeholder="Search for a country"
          class="form-control"
        />
      </div>
    </section>

    <!-- Countries List -->
    <section class="container py-5">
      <div class="row">
        <div
          v-for="(country, index) in countries"
          :key="index"
          class="col-md-3 mb-4"
        >
          <div class="card country-card shadow-sm border-0">
            <img
              :src="country.flags?.png"
              class="card-img-top"
              :alt="country.name.common"
              style="height: 150px; object-fit: cover; border-radius: 10px 10px 0 0;"
            />
            <div class="card-body">
              <h5 class="fw-bold">{{ country.name.common }}</h5>
              <p class="mb-1"><strong>Region:</strong> {{ country.region }}</p>
              <p class="mb-1"><strong>Capital:</strong> {{ country.capital?.[0] || "-" }}</p>
              <p class="mb-3">
                <strong>Population:</strong> {{ country.population.toLocaleString() }}
              </p>
              <button
                class="btn btn-warning btn-sm"
                @click="showDetails(country.name.common)"
              >
                More Info
              </button>
            </div>
          </div>
        </div>
      </div>

      <!-- Jika tidak ada data -->
      <div v-if="countries.length === 0" class="text-center mt-5">
        <p class="text-muted">No countries found.</p>
      </div>
    </section>

    <!-- Modal Detail -->
    <div
      class="modal fade"
      id="countryModal"
      tabindex="-1"
      aria-hidden="true"
      ref="countryModalRef"
    >
      <div class="modal-dialog modal-lg modal-dialog-centered">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title fw-bold">{{ selectedCountry?.name.common }}</h5>
            <button
              type="button"
              class="btn-close"
              data-bs-dismiss="modal"
              aria-label="Close"
            ></button>
          </div>
          <div class="modal-body" v-if="selectedCountry">
            <div class="row">
              <div class="col-md-5">
                <img
                  :src="selectedCountry.flags?.png"
                  :alt="selectedCountry.name.common"
                  class="img-fluid rounded"
                />
              </div>
              <div class="col-md-7">
                <p><strong>Official Name:</strong> {{ selectedCountry.name.official }}</p>
                <p><strong>Region:</strong> {{ selectedCountry.region }}</p>
                <p><strong>Subregion:</strong> {{ selectedCountry.subregion }}</p>
                <p><strong>Capital:</strong> {{ selectedCountry.capital?.[0] || "-" }}</p>
                <p><strong>Population:</strong> {{ selectedCountry.population.toLocaleString() }}</p>
                <p><strong>Area:</strong> {{ selectedCountry.area.toLocaleString() }} km²</p>
                <p><strong>Languages:</strong> {{ Object.values(selectedCountry.languages || {}).join(", ") }}</p>
                <p><strong>Currency:</strong>
                  {{ Object.values(selectedCountry.currencies || {}).map(c => c.name + " (" + c.symbol + ")").join(", ") }}
                </p>
                <p><strong>Timezones:</strong> {{ selectedCountry.timezones.join(", ") }}</p>
              </div>
            </div>
          </div>
          <div class="modal-footer">
            <button
              type="button"
              class="btn btn-secondary"
              data-bs-dismiss="modal"
            >
              Close
            </button>
          </div>
        </div>
      </div>
    </div>

    <!-- Footer -->
    <Footer />
  </div>
</template>

<script setup>
import { ref, onMounted, watch } from "vue";
import axios from "axios";
import { Modal } from "bootstrap";

const searchQuery = ref("");
const countries = ref([]);
const selectedCountry = ref(null);
let timeout = null;
let modalInstance = null;
const countryModalRef = ref(null);

// Ambil semua negara atau by name
const fetchCountries = async () => {
  try {
    let url =
      "https://restcountries.com/v3.1/all?fields=name,region,population,flags,capital,area";

    if (searchQuery.value.trim()) {
      url = `https://restcountries.com/v3.1/name/${searchQuery.value}?fields=name,region,population,flags,capital,area`;
    }

    const res = await axios.get(url);
    countries.value = res.data;
  } catch (error) {
    if (error.response && error.response.status === 404) {
      countries.value = [];
    } else {
      console.error("Error fetching countries:", error);
      countries.value = [];
    }
  }
};

// Detail negara
const showDetails = async (name) => {
  try {
    const res = await axios.get(`https://restcountries.com/v3.1/name/${name}`);
    selectedCountry.value = res.data[0];

    if (!modalInstance) {
      modalInstance = new Modal(countryModalRef.value);
    }
    modalInstance.show();
  } catch (error) {
    console.error("Error fetching country details:", error);
  }
};

// search
watch(searchQuery, () => {
  clearTimeout(timeout);
  timeout = setTimeout(() => {
    fetchCountries();
  }, 500);
});

// Load awal
onMounted(fetchCountries);
</script>

<style scoped>
.explore-hero {
  background-color: #ffd633;
  height: 250px;
}
.search-box {
  width: 350px;
  max-width: 100%;
}
.country-card {
  border: 2px solid #d3d3f3;
  border-radius: 10px;
}
</style>
