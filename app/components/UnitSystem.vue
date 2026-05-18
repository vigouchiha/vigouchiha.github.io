<template>
  <section class="unit-system-section">
    <div class="container">
      <h2 class="section-title">Unit System</h2>

      <div class="items-grid">
        <!-- Loop through the hardware items -->
        <div
          v-for="(item, index) in hardwareItems"
          :key="index"
          class="item-card"
        >
          <div class="image-wrapper">
            <img
              :src="item.image"
              :alt="item.name"
              class="item-img"
              @error="handleImgError"
            />
            <div class="image-placeholder">Hardware Image</div>
          </div>
          <h3 class="item-label">{{ item.name }}</h3>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
// Data for the components based on your design
const hardwareItems = [
  { name: "RTX 3060", image: "/vga_box.png" }, // MSI RTX 3060
  { name: "RTX 3060", image: "/motherboard.png" }, // ASRock Motherboard
  { name: "RTX 3060", image: "/cpu_box.png" }, // Intel i5 CPU
];

// Fallback logic if the images aren't found in the public folder yet
const handleImgError = (e) => {
  e.target.style.display = "none";
  e.target.nextElementSibling.style.display = "flex";
};
</script>

<style scoped>
/* Outer Wrapper */
.unit-system-section {
  width: 100%;
  padding: 4rem 2rem;
  background-color: #ffffff; /* Clean white background */
  display: flex;
  justify-content: center;
  box-sizing: border-box;
}

/* Constrain width and align contents */
.container {
  width: 100%;
  max-width: 1200px;
}

/* Section Title Typography */
.section-title {
  font-size: 2rem;
  font-weight: 400;
  color: #111111;
  margin-bottom: 3rem;
  font-family: "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
}

/* CSS Grid for the 3-column layout */
.items-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 4rem; /* Spacing between the items */
}

/* Individual Item Card */
.item-card {
  display: flex;
  flex-direction: column;
}

/* Image Container */
.image-wrapper {
  width: 100%;
  height: 350px; /* Fixed height ensures all images align nicely */
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 1.5rem;
}

/* Actual Image */
.item-img {
  width: 100%;
  height: 100%;
  object-fit: contain; /* Prevents stretching while filling the space */
}

/* Placeholder styles if images are missing */
.image-placeholder {
  display: none; /* Hidden by default, shown via script on error */
  width: 100%;
  height: 100%;
  background-color: #f0f0f0;
  border: 2px dashed #cccccc;
  align-items: center;
  justify-content: center;
  color: #666;
  font-weight: 500;
  border-radius: 8px;
}

/* Text Label below image */
.item-label {
  font-size: 1.5rem;
  font-weight: 400;
  color: #000000;
  font-family: "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  /* Matches the slight left-alignment relative to the visual weight of the images in the design */
  padding-left: 0.5rem;
}

/* Responsive adjustments for Tablets and Mobile */
@media (max-width: 992px) {
  .items-grid {
    gap: 2rem;
  }
  .image-wrapper {
    height: 250px;
  }
}

@media (max-width: 768px) {
  .items-grid {
    grid-template-columns: 1fr; /* Stack vertically on mobile */
    gap: 3rem;
  }

  .section-title {
    text-align: center;
  }

  .item-label {
    text-align: center;
    padding-left: 0;
  }
}
</style>
