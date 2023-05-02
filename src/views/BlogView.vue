<template>
  <h1>Blog</h1>
  <div v-if="error">
    {{ error }}
  </div>
  <div v-if="posts.length">
    <PostList v-if="showPosts" :posts="posts" />
  </div>
  <div v-else>Loading..</div>
  <button @click="showPosts = !showPosts">toggle posts</button>
  <button @click="posts.pop()">Delete post</button>
</template>

<script>
import PostList from "@/components/PostList.vue";
import getPosts from '../composables/getPosts'
import { ref } from "vue";

export default {
  name: "Blog",
  components: { PostList },

  setup() {
    const {posts, error, load} = getPosts()
    load();


    const showPosts = ref(true);
    return { posts, showPosts, error };
  },
};
</script>

<style></style>
