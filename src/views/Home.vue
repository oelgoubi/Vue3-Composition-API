<template>
  <div class="home">
    <h1>HOME</h1>
    <div class="error-show" v-if="error">
      <p>{{error}}</p>
    </div>
    <div class="spinner" v-if="posts.length">
      <PostList  :posts="posts" />
    </div>
    <div class="spinner" v-else>
      Data is Loading...
    </div>
    
  </div>
</template>

<script>
import PostList from '../components/PostList.vue'
import { ref } from "vue"
export default {
  name: 'Home',
  components : { PostList },
  setup(){
    const posts = ref([]);
    const error = ref(null);

    const load = async ()=>{
      try {
        let data = await fetch("http://localhost:3000/posts");
        if(!data.ok)
        {
          throw Error("Data is not available")
        }
        posts.value = await data.json();
        
      } catch (err) {
        error.value = err.message;
        console.log(error.value)
      }
    }

    load();
   
    return {posts,error}

  }
}
</script>
