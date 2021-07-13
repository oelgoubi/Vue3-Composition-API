<template>
  <div class="home">
    <h1>HOME</h1>
    <PostList  :posts="posts" v-if="showPosts" />
    <button @click="showPosts = !showPosts">toggle posts</button>
    <button @click="posts.pop()">delete post</button>
  </div>
</template>

<script>
import PostList from '../components/PostList.vue'
import { ref } from "vue"
export default {
  name: 'Home',
  components : { PostList },
  setup(){
    const posts = ref([
      { title:'welcome to the blog', body:"Lorem ipsum typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.", id:1},
      { title:'Top 5 CSS Tips', body:"Lorem ipsum typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.", id:2},
    ])
    const showPosts = ref(true);
   
    return {posts,showPosts}

  }
}
</script>
