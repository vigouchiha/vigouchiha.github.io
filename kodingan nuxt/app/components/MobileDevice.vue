<template>
  <div class="page-wrapper">
    <main class="container">
      <section class="profile-section">
        <div class="profile-image">
          <img
            src="/borutotimeskip.jpg"
            alt="Vigo Uchiha"
            class="profile-pic"
          />
        </div>
        <div class="profile-detail">
          <h1 class="name">Vigo Uchiha</h1>
          <h2 class="title">Content Creator</h2>
          <p class="tagline">We have to be greater than what we suffer</p>
        </div>
      </section>

      <div class="social-links">
        <div class="social-icon">
          <a href="https://www.youtube.com/@vigouchiha" target="_blank"
            ><img class="youtube" src="/youtube.png" alt="YouTube"
          /></a>
        </div>

        <div class="social-icon">
          <a href="https://www.tiktok.com/@vigouchiha" target="_blank"
            ><img src="/tiktok.png" alt="TikTok"
          /></a>
        </div>
        <div class="social-icon">
          <a href="https://www.instagram.com/vigouchiha" target="_blank"
            ><img src="/instagram.png" alt="Instagram"
          /></a>
        </div>
        <div class="social-icon">
          <a href="https://discord.gg/SnxYymWX" target="_blank"
            ><img src="/discord.png" alt="Discord"
          /></a>
        </div>
        <!-- <div class="social-icon">
          <a href="#"><img src="/linkedin.png" alt="LinkedIn" /></a>
        </div> -->
      </div>

      <!-- <nav class="tabs">
        <button
          v-for="tab in tabs"
          :key="tab"
          @click="activeTab = tab"
          :class="['tab', { active: activeTab === tab }]"
        >
          {{ tab }}
        </button>
      </nav> -->

      <!-- <section class="banner-section">
        <div class="banner">
          <div class="banner-container">
            <img
              src="/gaming_setup.jpg"
              alt="Product Shirt"
              class="product-img"
            />
          </div>
        </div>
        <div class="banner2"></div>
        <div class="banner3"></div>
      </section> -->
      <section class="donation">
        <a href=https://saweria.co/vigouchiha class="saweria"target="_blank" >
          saweria
        </a>

        <a href="https://sociabuzz.com/vigouchiha/tribe" class="socialbuzz"target="_blank">
          sociabuzz
        </a>
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
@import url("~/assets/css/mobile.css");
</style>
