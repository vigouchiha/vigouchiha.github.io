<script setup>
import { ref, computed, watch } from "vue";

// 1. STATE DASAR (Diubah oleh input user di layar)
const selectedBrand = ref("Toyota");
const maxPrice = ref(300000000);
const isAutomatic = ref(true);

// 2. COMPUTED: Sang Akuntan
// Tugasnya murni merakit ketiga state di atas menjadi satu URL Query String yang rapi
const apiQueryString = computed(() => {
  // Hasilnya akan seperti: "?brand=Toyota&price=300000000&auto=true"
  return `?brand=${selectedBrand.value}&price=${maxPrice.value}&auto=${isAutomatic.value}`;
});

// 3. WATCH: Sang Manajer
// Mengawasi hasil akhir dari Computed, bukan mengawasi state satu per satu
watch(
  apiQueryString,
  async (newQuery, oldQuery) => {
    console.log(
      `Filter berubah! Mengambil data dari server dengan URL: ${newQuery}`,
    );

    // Lakukan pemanggilan API (Efek Samping)
    try {
      // isLoading.value = true
      // const response = await fetch(`https://api.website-mobil.com/search${newQuery}`)
      // carList.value = await response.json()
    } catch (error) {
      console.error("Gagal mengambil data mobil", error);
    } finally {
      // isLoading.value = false
    }
  },
  { immediate: true },
);
// Catatan: { immediate: true } memaksa watch untuk langsung berjalan satu kali
// saat halaman pertama kali dimuat, agar list mobil langsung muncul tanpa menunggu user mengubah filter.
</script>
