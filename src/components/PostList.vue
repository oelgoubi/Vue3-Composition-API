<template>
  <div class="post-list">
      <div v-for="post in posts" :key="post.id">
          <SinglePost :post="post" />
      </div>
  </div>
</template>

<script>
import { onMounted, onUnmounted, onUpdated } from '@vue/runtime-core'
import SinglePost from './SinglePost.vue'
export default {
    name:'PostList',
    components : {SinglePost},
    props: ["posts"],
    setup(props){
        onMounted(()=>{
            console.log("OnMounted")
        })
         onUnmounted(()=>{
            console.log("On UnMounted")
        })

        // This will fire once the data coming from the parent changes or the current data in the component
        onUpdated(()=>{
            console.log("on Updated")
        })
        
    },
    mounted(){
        console.log("mounted using options api")
    }
}
</script>

<style>

</style>

