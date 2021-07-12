<template>
  <div class="home">
    <h1>Hello</h1>
    <p>My NAME is {{name}} and my age is {{age}}</p>
    <button @click="handleClick">Click me</button>
  </div>
</template>

<script>
import { ref } from "vue"
export default {
  name: 'Home',
  // Setup Hook That execute before all the cycle hooks
  // This keyword is not available inside the Setup Hook
  setup(){
    console.log('setup');
    //const p = ref(null);// p.value will be undefined untill we return it from the setup function
    // Ref is const but the value can change
    const name = ref("Sami"), age = ref(12);

    const handleClick = ()=>{
      name.value = "Othy"
      age.value = 22
    }

    return { name, age,handleClick }

  }
}
</script>
