<template>
  <div class="home">
    <h1>Home</h1>
    <div>
      <h1>Orang Pertama</h1>
      <p>Nama : {{ orangPertama.name }}</p>
      <p>Umur : {{ orangPertama.age }}</p>
    </div>
    <div>
      <h1>Orang Kedua</h1>
      <p>Nama : {{ orangKedua.name }}</p>
      <p>Umur : {{ orangKedua.age }}</p>
    </div>
    <p>{{ alamat }}</p>
    <button @click="ubahOrangPertama">Ubah nama orang pertama bang</button>
    <button @click="ubahOrangKedua">Ubah nama orang kedua bang</button>
  </div>
</template>

<script>
import { reactive, ref } from "@vue/reactivity";
export default {
  setup() {
    // In our mind may think why we dont use just reactivity instead using ref. Ref look so terible, when we want to access the value of the property we must access the value property first and then we got the value. If we use reactive we just need write the variable name only. But the reactivity has drawback, if we use reactivity we cant assign the primitif value inside of the variable. The things gonna be clear if we see the example below :

    let orangPertama = ref({ name: "Gautama", age: 17 });
    let orangKedua = reactive({ name: "Rama", age: 20 });

    let alamat = reactive("Jl. Kenari No. 27");

    const ubahOrangPertama = () => {
      orangPertama.value.name = "Tama";
    };

    const ubahOrangKedua = () => {
      orangKedua.name = "Amar";
      // alamat = "Jl. ASemloHoy No. 28"; // cannot do this brow // Kalau mau ganti value reactive maka yang boleh diassign di dalam function reactive ini adalah object, bukan data primitive seperti diatas begitu everybody.
    };

    return { orangPertama, orangKedua, ubahOrangPertama, ubahOrangKedua, alamat };
  },
};
</script>
