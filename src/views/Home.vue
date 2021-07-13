<template>
  <div class="home">
    <h1>Hello</h1>
    <input type="text" v-model="search">
    <p>Search term - {{ search }}</p>
    <div v-for="name in matchingNames" :key="name">
        <p>{{name}}</p>
    </div>
    <button @click="stopWatching">stop Watching</button>
  </div>
</template>

<script>
import { computed,ref, watch, watchEffect } from "vue"
export default {
  name: 'Home',
  setup(){
    const search = ref('');
    const names = ref(['nano','bobo','show','jiki'])

    // Runs whenever "search" changes
    const stopWatch = watch(search,()=>{
      console.log("Search changes")
    })

    // Runs whenever a variable is defined inside the function changes and
    // Runs once before the creation of the components (Get Data from DB)
    const stopWatchEffect = watchEffect(()=>{
      console.log("Watch Effect",search.value)
    })
    const matchingNames = computed(()=>{
      return names.value.filter((name)=>{
        // Return words that include the searching chars
        return name.includes(search.value)
      })
    })

    // Stop Watching by storing them in a variable and call the function;
    const stopWatching = ()=>{
      // Invoke the functions
      stopWatch();
      stopWatchEffect();
    }
    
    return {names,search,matchingNames,stopWatching}

  }
}
</script>
