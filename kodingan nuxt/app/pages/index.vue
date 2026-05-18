<template>
  <div :class="['app-wrapper', { 'dark-theme': isDarkMode }]">
    <!-- Header Navigation -->
    <header class="navbar">
      <div class="nav-container">
        <!-- Grey Box Placeholder -->
        <div class="logo-box"></div>

        <!-- Navigation Links -->
        <nav class="nav-links">
          <a href="#" class="nav-item">Beranda</a>
          <a href="#" class="nav-item">Activities</a>
          <a href="#" class="nav-item">Contact</a>
        </nav>

        <!-- Theme Toggle -->
        <div class="theme-toggle">
          <span class="theme-label">Light</span>
          <label class="switch">
            <input
              type="checkbox"
              :checked="isDarkMode"
              @change="toggleTheme"
            />
            <span class="slider"></span>
          </label>
          <span class="theme-label">Dark</span>
        </div>
      </div>
    </header>

    <!-- Main Hero Section -->
    <main class="hero-section">
      <div class="hero-container">
        <!-- Left Content: Typography and Socials -->
        <div class="hero-text">
          <h1 class="title">VIGO UCHIHA</h1>
          <h2 class="subtitle">Content Creator</h2>
          <p class="quote">“We have to be greater than what we suffer”</p>

          <div class="social-grid">
            <a
              href="#"
              v-for="social in socialLinks"
              :key="social.name"
              class="social-item"
            >
              <div class="social-icon-wrapper">
                <img
                  :src="social.icon"
                  :alt="social.name"
                  class="social-icon"
                />
              </div>
              <span class="social-name">{{ social.name }}</span>
            </a>
          </div>
        </div>

        <!-- Right Content: Character Image -->
        <div class="hero-image">
          <img src="" alt="Character Illustration" />
        </div>
      </div>
    </main>
  </div>
  <ProductDetail />
  <DeviceShowcase />
  <MerchSection />
  <ProductCatalog />
  <UnitSystem />
</template>
<style scoped>
@import url("~/assets/css/index.css");
</style>
<script setup>
import { ref, onMounted, watch } from "vue";
import ProductDetail from "~/components/ProductDetail.vue";

const isDarkMode = ref(false);

// Toggle function for the switch
const toggleTheme = () => {
  isDarkMode.value = !isDarkMode.value;
};

// Persist theme preference in localStorage
onMounted(() => {
  if (process.client) {
    const savedTheme = localStorage.getItem("theme");
    if (savedTheme === "dark") {
      isDarkMode.value = true;
    }
  }
});

watch(isDarkMode, (newValue) => {
  if (process.client) {
    localStorage.setItem("theme", newValue ? "dark" : "light");
  }
});

// Social links data
const socialLinks = [
  {
    name: "Linkedin",
    icon: "https://cdn-icons-png.flaticon.com/512/174/174857.png",
  },
  {
    name: "Instagram",
    icon: "https://cdn-icons-png.flaticon.com/512/2111/2111463.png",
  },
  {
    name: "Tiktok",
    icon: "https://cdn-icons-png.flaticon.com/512/3046/3046120.png",
  },
  {
    name: "Youtube",
    icon: "https://cdn-icons-png.flaticon.com/512/1384/1384060.png",
  },
];
</script>
