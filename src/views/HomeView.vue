<template>
  <div class="home">
    <h1>Home</h1>
    <p v-for="list in searchResult" :key="list">{{ list }}</p>
    <input type="text" v-model="input" />
    <p>{{ input }}</p>
  </div>
</template>

<script>
import { reactive, ref } from "@vue/reactivity";
import { computed, watch, watchEffect } from "@vue/runtime-core";
export default {
  setup() {
    let lists = ref(["mario", "luigi", "bouser", "peach"]);
    let input = ref("");
    let searchResult = computed(() => {
      return lists.value.filter((list) => {
        return list.includes(input.value);
      });
    });

    const watchOnly = watch(input, (newValue, oldValue) => {
      if (newValue == "mario") {
        input.value = "luigi";
        console.log(oldValue);
      }
    });

    // Oke jadi gini, sekarang kita pakai bahasa indonesia aja ya biar enak aja mewhheeheh. Apa sih sebenarnya perbedaan antara watch dan watchEffect. watch itu berfungsi untuk memantau suatu properti jika terdapat perubahan kemudian mengeksekusi kode yang telah ditulis, terus apa bedanya ngap sama computed. Bedanya, computed itu menghasilkan value yang baru sedangkan kalo watch itu berfungsi untuk melihat namun tidak secara eksplisit membuat value yang baru. Oke kita balik lagi ke watch, watch sendiri meneri 3 parameter yang pertama properti yang mau diwatch, kemudian kita dapat menaruh callback disana yang ada dua paramater yaitu newValue dan oldValue, fungsi kedua parameter ini sih untuk mendapatkan value dari properti yang bersangkutan. Lanjut ke watch effect, apa sih watch effect, watch effect sendiri itu kurang lebih sama kyk watch cuma kalo watch effect ini akan dijalankan saat pertama kali ketika component mounted dan ketika suatu properti yang dipantau berubah. Lah, selain itu ada ngga beda nya ngab. Tentu ada dong, kalau watch itu hanya mantau satu properti doang, kalo properti tersebut ngga berubah otomatis kode pun ngga akan dieksekusi, terus kalo watcheffect dia akan mantau semua perubahan yang ada didalem functionnya, misal kalo didalam watcheffect ada pengkondisian yang akan dijalankan ketika salah satu dari dua properti yang dipantau berubah, maka secara langsung watch akan mantau dua duanya, beda degan watch yang hanya memeriksa perubahan satu properti yang ditulis aja begitu.

    const watchEff = watchEffect(() => {
      console.log("Watch effect berjalan", input.value);
    });

    // Untuk mengstop watch dan watchEffect kita dapat menyimpat watch dan Watcheffect  itu ke sebuah variabel yang nantinya kita panggil supaya tidak dijalankan lagi

    watchEff();
    watchOnly();

    return { searchResult, input, lists };
  },
};
</script>
