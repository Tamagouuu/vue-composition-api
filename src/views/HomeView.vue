<template>
  <div class="home">
    <h1>This is {{ page }}</h1>
    <h3>Welcome {{ name }}, your age must be {{ age }}</h3>
    <button @click="age++">Click this, if you want go older 👴</button>
    <p>Hi i am paragraph text</p>
    <input type="text" v-model="name" />
    <button @click="handleClick">Click me plz !</button>
  </div>
</template>

<script>
import { ref } from "@vue/reactivity";
export default {
  setup() {
    let page = ref("Homepage");
    let name = ref("Gautama");

    // let p = ref(null);

    // As we know before that ref's is used to refrence some element in html which mean the usage of ref is limited, but in composition api we use ref for reactivity too, because in setup life cycle we dont have this for refrence our component and if we wanted to change the value of the property it will be doesnt work like what we expected when we use option api, so we use ref for the reactivity. But one thing that you should do when you use ref as reactivity value, if we want to access the value of the property we must add .value property to access the actual value, but if we access the property from template we just need to write the property name. (I think it's the same case like we use property in option API when we want to reffering property we use keyword this before the property name)

    let age = ref(17);

    const handleClick = () => {
      // p.value.innerText = "You just clicked me :p";
      name.value = "Tama";
    };

    return { page, name, handleClick, age };
  },
};
</script>
