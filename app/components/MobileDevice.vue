<template>
  <div class="page-wrapper">
    <main class="mobile-container">
      <section class="profile-section">
        <img
          src="https://via.placeholder.com/150/5a55ca/ffffff?text=VU"
          alt="Vigo Uchiha"
          class="profile-pic"
        />
        <h1 class="name">Vigo Uchiha</h1>
        <h2 class="title">Content Creator</h2>
        <p class="tagline">We have to be greater than what we suffer</p>
      </section>

      <div class="social-links">
        <a href="#" class="social-icon yt">▶</a>
        <a href="#" class="social-icon tk">♪</a>
        <a href="#" class="social-icon ig">◎</a>
        <a href="#" class="social-icon in">in</a>
      </div>

      <nav class="nav-tabs">
        <button
          v-for="tab in tabs"
          :key="tab"
          @click="activeTab = tab"
          :class="['tab', { active: activeTab === tab }]"
        >
          {{ tab }}
        </button>
      </nav>

      <section class="carousel-section">
        <button class="nav-arrow arrow-left">&#10094;</button>
        <img
          src="https://via.placeholder.com/300x350/111111/ffffff?text=T-Shirt+Graphic"
          alt="Product Shirt"
          class="product-img"
        />
        <button class="nav-arrow arrow-right">&#10095;</button>
      </section>

      <section class="banner-section">
        <img
          src="https://via.placeholder.com/400x200/1e1e40/ffffff?text=Gaming+Setup"
          alt="Gaming Setup"
          class="banner-img"
        />

        <div class="banner-content">
          <h3>Good Device</h3>
          <p>Device improve your movement</p>
          <button class="btn-more">More information</button>
        </div>
      </section>
    </main>
  </div>
</template>

<script setup>
import { ref } from "vue";

// State untuk mengatur tab yang aktif
const tabs = ref(["Beranda", "Shop", "Gaming Gear"]);
const activeTab = ref("Beranda");
</script>

<style scoped>
/* --- BASE & TYPOGRAPHY --- */
.page-wrapper {
  --lh-golden: 1.618;
  --primary-purple: #6a5acd;
  --text-dark: #111111;
  --text-muted: #555555;
  --bg-light: #ffffff;
  --bg-app: #f4f4f9;

  background-color: var(--bg-app);
  color: var(--text-dark);
  font-family: "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  line-height: var(--lh-golden);
  min-height: 100vh;
  display: flex;
  justify-content: center;
}

/* Mobile Container Simulator */
.mobile-container {
  width: 100%;
  max-width: 420px; /* Lebar maksimum standar Android kecil */
  background-color: var(--bg-light);
  padding: 30px 20px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
  overflow-x: hidden;
}

/* --- PROFILE SECTION --- */
.profile-section {
  text-align: center;
  margin-bottom: 20px;
}

.profile-pic {
  width: 120px;
  height: 120px;
  border-radius: 50%;
  object-fit: cover;
  margin: 0 auto 15px;
  display: block;
}

.name {
  font-size: 26px; /* Golden Ratio Title (H3 basis 16) */
  font-weight: 600;
  margin-bottom: 2px;
}

.title {
  font-size: 16px;
  font-weight: 500;
  margin-bottom: 8px;
}

.tagline {
  font-size: 13px;
  color: var(--text-muted);
  margin-bottom: 20px;
}

/* --- SOCIAL LINKS --- */
.social-links {
  display: flex;
  justify-content: center;
  gap: 12px;
  margin-bottom: 25px;
}

.social-icon {
  width: 32px;
  height: 32px;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-weight: bold;
  text-decoration: none;
  font-size: 18px;
}

.yt {
  background: #ff0000;
  border-radius: 50%;
}
.tk {
  background: #000000;
}
.ig {
  background: radial-gradient(
    circle at 30% 107%,
    #fdf497 0%,
    #fdf497 5%,
    #fd5949 45%,
    #d6249f 60%,
    #285aeb 90%
  );
  border-radius: 50%;
}
.in {
  background: #0077b5;
}

/* --- NAVIGATION TABS --- */
.nav-tabs {
  display: flex;
  justify-content: center;
  gap: 15px;
  margin-bottom: 25px;
}

.tab {
  font-size: 14px;
  font-weight: 500;
  color: var(--text-dark);
  background: transparent;
  border: none;
  cursor: pointer;
  padding: 6px 16px;
  border-radius: 20px;
  transition: all 0.2s ease;
  font-family: inherit;
}

.tab.active {
  background-color: var(--primary-purple);
  color: white;
}

/* --- CAROUSEL SECTION --- */
.carousel-section {
  position: relative;
  width: 100%;
  margin-bottom: 30px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.product-img {
  width: 80%;
  max-width: 280px;
  height: auto;
  object-fit: contain;
}

.nav-arrow {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: 36px;
  height: 36px;
  background-color: rgba(220, 220, 220, 0.8);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  border: none;
  font-size: 18px;
  color: #333;
}

.arrow-left {
  left: 0;
}
.arrow-right {
  right: 0;
}

/* --- BANNER SECTION --- */
.banner-section {
  position: relative;
  width: 100%;
  border-radius: 12px;
  overflow: hidden;
  background-color: #000;
}

.banner-img {
  width: 100%;
  height: 160px;
  object-fit: cover;
  opacity: 0.8;
  display: block;
}

.banner-content {
  position: absolute;
  top: 50%;
  right: 20px;
  transform: translateY(-50%);
  width: 55%;
  text-align: left;
  color: white;
}

.banner-content h3 {
  font-size: 18px;
  margin-bottom: 4px;
}

.banner-content p {
  font-size: 11px;
  line-height: 1.4;
  margin-bottom: 12px;
}

.btn-more {
  background-color: white;
  color: black;
  border: none;
  padding: 6px 12px;
  border-radius: 15px;
  font-size: 10px;
  font-weight: 600;
  cursor: pointer;
}
</style>
