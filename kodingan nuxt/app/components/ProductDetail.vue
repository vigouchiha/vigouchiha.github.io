<template>
  <section class="product-page-wrapper">
    <div class="product-container">
      <!-- Left Column: Product Images -->
      <div class="left-column">
        <!-- Main Image -->
        <div class="main-image-wrapper">
          <img
            src="/product_main.webp"
            alt="Men's Grey T-Shirt"
            class="main-image"
            @error="handleImgError"
          />
          <div class="image-placeholder">Main Product Image</div>
        </div>

        <!-- Thumbnails -->
        <div class="thumbnail-gallery">
          <div v-for="n in 5" :key="n" class="thumbnail-wrapper">
            <!-- Simulating 3 images and 2 empty slots as seen in design -->
            <img
              v-if="n <= 3"
              :src="`/product_thumb_${n}.webp`"
              alt="Thumbnail"
              class="thumbnail-image"
              @error="handleImgError"
            />
            <div class="thumbnail-placeholder"></div>
          </div>
        </div>
      </div>

      <!-- Right Column: Product Details -->
      <div class="right-column">
        <!-- Size Guide Section -->
        <div class="size-guide-section">
          <!-- T-Shirt Illustration -->
          <div class="size-diagram-wrapper">
            <img
              src="/tshirt_diagram.jfif"
              alt="Size Guide Diagram"
              class="size-diagram"
              @error="handleImgError"
            />
            <div class="diagram-placeholder">Diagram</div>
          </div>

          <!-- Size Chart Table -->
          <div class="size-table-wrapper">
            <table class="size-table">
              <thead>
                <tr>
                  <th>Size</th>
                  <th
                    v-for="(size, index) in tableData.sizes"
                    :key="size"
                    :style="{ backgroundColor: tableData.colors[index] }"
                  >
                    {{ size }}
                  </th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="row in tableData.measurements" :key="row.label">
                  <td>{{ row.label }}</td>
                  <td
                    v-for="(val, index) in row.values"
                    :key="index"
                    :style="{ backgroundColor: tableData.colors[index] }"
                  >
                    {{ val }}
                  </td>
                </tr>
              </tbody>
            </table>
            <p class="tolerance-text">Toleransi ukuran 1 - 2,5 cm</p>
          </div>
        </div>

        <!-- Description -->
        <div class="detail-section">
          <h3 class="section-title">Deskripsi</h3>
          <p class="section-text">
            Made from lightweight ring-spun cotton, this t-shirt offers a
            noticeably softer and more comfortable feel. It features a regular
            fit that sits nicely without feeling tight. A versatile choice for
            relaxed days or clean, casual looks.
          </p>
        </div>

        <!-- Location -->
        <div class="detail-section">
          <h3 class="section-title">Lokasi pengiriman</h3>
          <p class="section-text">Kedoya, Jakarta Barat</p>
        </div>

        <!-- Price -->
        <div class="price-section">Rp.100.000</div>

        <!-- Action Buttons -->
        <div class="action-buttons">
          <button class="shop-btn tiktok-btn">
            <img
              src="/tiktok_shop_logo.webp"
              alt="TikTok Shop"
              class="btn-logo"
              @error="handleImgError"
            />
            <span class="btn-placeholder text-black">TikTok Shop</span>
          </button>

          <button class="shop-btn whatsapp-btn">
            <img
              src="/whatsapplogo.webp"
              alt="WhatsApp"
              class="btn-logo"
              @error="handleImgError"
            />
            <span class="btn-placeholder text-black">WhatsApp</span>
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
// Data for the colorful size table
const tableData = {
  sizes: ["S", "L", "XL", "2XL", "3XL", "4XL", "5XL"],
  // The exact column colors from your design
  colors: [
    "#fcdcb4",
    "#b6e5e8",
    "#f8b3ed",
    "#b6f6b5",
    "#fbf0aa",
    "#b5b2f8",
    "#f8a8a9",
  ],
  measurements: [
    { label: "P", values: [47, 47, 47, 47, 47, 47, 47] },
    { label: "L", values: [47, 47, 47, 47, 47, 47, 47] },
    { label: "LD", values: [47, 47, 47, 47, 47, 47, 47] },
  ],
};

// Fallback logic if images aren't found in the public folder yet
const handleImgError = (e) => {
  e.target.style.display = "none";
  if (e.target.nextElementSibling) {
    e.target.nextElementSibling.style.display = "flex";
  }
};
</script>

<style scoped>
/* Outer Wrapper */
.product-page-wrapper {
  width: 100%;
  padding: 3rem 2rem;
  background-color: #ffffff;
  display: flex;
  justify-content: center;
  box-sizing: border-box;
  font-family: "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
}

/* Main Container (Flexbox) */
.product-container {
  width: 100%;
  max-width: 1100px;
  display: flex;
  gap: 3rem;
}

/* --- Left Column (Images) --- */
.left-column {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.main-image-wrapper {
  width: 100%;
  aspect-ratio: 1; /* Makes it a perfect square */
  background-color: #e5e5e5;
  display: flex;
  justify-content: center;
  align-items: center;
}

.main-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.image-placeholder {
  display: none;
  color: #666;
}

.thumbnail-gallery {
  display: flex;
  justify-content: space-between;
  gap: 10px;
}

.thumbnail-wrapper {
  flex: 1;
  aspect-ratio: 1;
  background-color: #dcdcdc;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}

.thumbnail-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.thumbnail-placeholder {
  width: 100%;
  height: 100%;
  background-color: #dcdcdc; /* Matches the empty grey squares in design */
}

/* --- Right Column (Details) --- */
.right-column {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

/* Size Guide Section */
.size-guide-section {
  display: flex;
  gap: 1.5rem;
  align-items: flex-start;
}

.size-diagram-wrapper {
  flex: 0 0 150px; /* Fixed width for the diagram */
  display: flex;
  justify-content: center;
  align-items: center;
}

.size-diagram {
  width: 100%;
  height: auto;
  object-fit: contain;
}

.diagram-placeholder {
  display: none;
  width: 100%;
  height: 150px;
  background-color: #f0f0f0;
  border: 1px dashed #ccc;
  align-items: center;
  justify-content: center;
  font-size: 0.8rem;
}

/* Colorful Size Table */
.size-table-wrapper {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: flex-end;
}

.size-table {
  width: 100%;
  border-collapse: collapse;
  text-align: center;
  font-size: 0.9rem;
}

.size-table th,
.size-table td {
  padding: 6px 4px;
  color: #111;
}

.size-table th {
  font-weight: 400;
}

.size-table td:first-child,
.size-table th:first-child {
  text-align: left;
  background-color: transparent !important;
  font-weight: 400;
}

.tolerance-text {
  font-size: 0.75rem;
  color: #555;
  margin-top: 0.5rem;
}

/* Description & Location */
.detail-section {
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
}

.section-title {
  font-size: 1rem;
  font-weight: 500;
  color: #111;
  margin: 0;
}

.section-text {
  font-size: 0.95rem;
  color: #333;
  line-height: 1.5;
  margin: 0;
}

/* Price */
.price-section {
  font-size: 1.1rem;
  font-weight: 500;
  color: #111;
}

/* Action Buttons */
.action-buttons {
  display: flex;
  gap: 2rem;
  margin-top: 1rem;
}

.shop-btn {
  background: transparent;
  border: none;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0;
  transition: transform 0.2s ease;
}

.shop-btn:hover {
  transform: scale(1.05);
}

.btn-logo {
  height: 45px; /* Adjust based on your actual logo images */
  width: auto;
  object-fit: contain;
}

.btn-placeholder {
  display: none;
  padding: 10px 20px;
  background-color: #f0f0f0;
  border-radius: 8px;
  font-weight: 600;
}

/* --- Responsive Adjustments --- */
@media (max-width: 768px) {
  .product-container {
    flex-direction: column;
  }

  .size-guide-section {
    flex-direction: column;
    align-items: center;
  }

  .size-table-wrapper {
    width: 100%;
    align-items: center;
  }

  .action-buttons {
    flex-direction: column;
    align-items: center;
    gap: 1rem;
  }
}
</style>
