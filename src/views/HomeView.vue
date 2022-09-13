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
import { computed } from "@vue/runtime-core";
export default {
  setup() {
    let lists = ref(["mario", "luigi", "bouser", "peach"]);
    let input = ref("");
    let searchResult = computed(() => {
      return lists.value.filter((list) => {
        return list.includes(input.value);
      });
    });
    return { searchResult, input, lists };
  },
};
</script>
