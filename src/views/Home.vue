<template>
  <div class="home">
    <h1>REF</h1>
    <p>My NAME is {{ninja.name}} and my age is {{ninja.age}}</p>
    <button @click="handleClick">Click me</button>
    <button @click="ninja.age++">Increase age</button>
    <input type="text" v-model="ninja.name">
    <h1>Reactive</h1>
    <p>My NAME is {{ninja2.name}} and my age is {{ninja2.age}}</p>
    <button @click="handleClick2">Click me</button>
  </div>
</template>

<script>
import { ref,reactive } from "vue"
export default {
  name: 'Home',
  // Setup Hook That execute before all the cycle hooks
  // This keyword is not available inside the Setup Hook
  setup(){
    console.log('setup');
    //const p = ref(null);// p.value will be undefined untill we return it from the setup function
    // Ref is const but the value can change
    const ninja = ref({ name:'mario', age: 24 });
    const ninja2 = reactive({ name:'Othy', age: 12 });// We can't use it with primitve values

    const handleClick = ()=>{
      ninja.value.name = "Othy"
      ninja.value.age = 22
    }

    const handleClick2 = ()=>{
      ninja2.age = 69
    }

    return {ninja,handleClick,handleClick2,ninja2 }

  }
}
</script>
