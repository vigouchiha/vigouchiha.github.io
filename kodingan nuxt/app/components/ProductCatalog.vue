<template>
  <section class="catalog-wrapper">
    <!-- Top Header -->
    <header class="catalog-header">
      <h2>KREASI TANPA BATAS</h2>
    </header>

    <div class="catalog-container">
      <!-- Left Sidebar (Filters) -->
      <aside class="sidebar">
        <div class="breadcrumb">Anime &gt; All</div>

        <h3 class="filter-heading">Filter</h3>

        <div class="filter-menu">
          <!-- Active Expanded Menu Item -->
          <div class="menu-item active">
            <div class="menu-header">
              <span>Anime</span>
              <button class="arrow-btn">v</button>
            </div>
            <ul class="submenu">
              <li class="submenu-item active-sub">All</li>
              <li class="submenu-item">Naruto</li>
            </ul>
          </div>

          <!-- Inactive Menu Items -->
          <div
            class="menu-item"
            v-for="menu in ['Games', 'Sport', 'Others']"
            :key="menu"
          >
            <div class="menu-header">
              <span>{{ menu }}</span>
              <button class="arrow-btn">&gt;</button>
            </div>
          </div>
        </div>
      </aside>

      <!-- Right Content (Product Grid) -->
      <main class="product-area">
        <div class="product-grid">
          <!-- Product Cards Loop -->
          <article
            v-for="(product, index) in products"
            :key="index"
            class="product-card"
          >
            <div class="image-wrapper">
              <img
                :src="product.image"
                :alt="product.name"
                class="product-img"
                @error="handleImgError"
              />
              <div class="image-placeholder">Product Image</div>
            </div>
            <h4 class="product-title">{{ product.name }}</h4>
            <p class="product-price">{{ product.price }}</p>
          </article>
        </div>
      </main>
    </div>
  </section>
</template>

<script setup>
// Mock data for the products shown in the design
const products = [
  {
    name: "Obito Uchiha",
    price: "Rp.100.000",
    image: "/tshirt_obito_1.png", // Replace with your actual image path
  },
  {
    name: "Obito Uchiha",
    price: "Rp.100.000",
    image: "/tshirt_obito_2.png", // Replace with your actual image path
  },
];

// Fallback logic if the images aren't found in the public folder yet
const handleImgError = (e) => {
  e.target.style.display = "none";
  e.target.nextElementSibling.style.display = "flex";
};
</script>

<style scoped>
/* Outer Wrapper */
.catalog-wrapper {
  width: 100%;
  padding: 3rem 2rem;
  background-color: #ffffff;
  display: flex;
  flex-direction: column;
  align-items: center;
  box-sizing: border-box;
  font-family: "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
}

/* Header Banner */
.catalog-header {
  width: 100%;
  text-align: center;
  margin-bottom: 3rem;
}

.catalog-header h2 {
  font-size: 1.8rem;
  font-weight: 400;
  color: #111;
  text-transform: uppercase;
  letter-spacing: 1px;
}

/* Main Layout Container */
.catalog-container {
  width: 100%;
  max-width: 1200px;
  display: flex;
  gap: 4rem; /* Space between sidebar and grid */
}

/* --- Sidebar Styles --- */
.sidebar {
  flex: 0 0 250px; /* Fixed width sidebar */
  display: flex;
  flex-direction: column;
}

.breadcrumb {
  font-size: 1.2rem;
  font-weight: 400;
  color: #111;
  margin-bottom: 1rem;
}

.filter-heading {
  font-size: 1.5rem;
  font-weight: 400;
  margin-bottom: 1rem;
  color: #111;
}

.filter-menu {
  background-color: #e5e7eb; /* Light grey background matching design */
  display: flex;
  flex-direction: column;
}

.menu-item {
  border-bottom: 1px solid #d1d5db; /* Subtle separators */
}

.menu-item:last-child {
  border-bottom: none;
}

.menu-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 12px 16px;
  font-size: 1rem;
  color: #333;
}

/* The small grey arrow buttons */
.arrow-btn {
  background-color: #9ca3af;
  color: #111;
  border: none;
  width: 24px;
  height: 24px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.8rem;
  cursor: pointer;
  font-family: monospace; /* Best for clean > and v characters */
}

/* Expanded submenu */
.submenu {
  list-style: none;
  padding: 0 0 12px 0;
  margin: 0;
}

.submenu-item {
  padding: 8px 16px;
  color: #444;
  font-size: 0.95rem;
  cursor: pointer;
}

.submenu-item:hover,
.submenu-item.active-sub {
  color: #000;
}

/* --- Product Grid Styles --- */
.product-area {
  flex: 1;
}

.product-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 3rem;
}

/* Individual Product Card */
.product-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.image-wrapper {
  width: 100%;
  aspect-ratio: 4 / 5; /* Approximate aspect ratio of the shirts */
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 1.5rem;
}

.product-img {
  width: 100%;
  height: 100%;
  object-fit: contain;
}

/* Fallback grey box if image is missing */
.image-placeholder {
  display: none;
  width: 100%;
  height: 100%;
  background-color: #f3f4f6;
  border: 1px dashed #ccc;
  align-items: center;
  justify-content: center;
  color: #666;
}

/* Product Typography */
.product-title {
  font-size: 1.3rem;
  font-weight: 400;
  color: #111;
  margin-bottom: 0.5rem;
}

.product-price {
  font-size: 1.3rem;
  font-weight: 400;
  color: #111;
}

/* --- Responsive Adjustments --- */
@media (max-width: 992px) {
  .catalog-container {
    gap: 2rem;
  }
}

@media (max-width: 768px) {
  .catalog-container {
    flex-direction: column; /* Stack sidebar on top of products on mobile */
  }

  .sidebar {
    flex: none;
    width: 100%;
    margin-bottom: 2rem;
  }

  .product-grid {
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 2rem;
  }
}
</style>
