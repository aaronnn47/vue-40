<template>
  <div>
    <h1>Bob Loblaws Blog App</h1>
    <button @click='switchView(true)'>Create</button>
    <button @click='switchView(false)'>Posts</button>

    <section v-if='showForm'>
      <h4>Create Post</h4>
      <p>Author: <input v-model='author' type="text"></p>
      <textarea v-model='postInput' name="" id="" cols="30" rows="10"></textarea>
      <button @click='addPost'>Create Post</button>
    </section>

    <section v-else>
      <h4>All Posts</h4>
      
      <post 
        v-for='(post, i) in allPosts'
        :key='i'
        :postObject='post'
        />

    </section>
    
  </div>
</template>

<script>
import Post from './components/Post';

export default {
  data() {
    return {
      showForm: true,
      author: '',
      postInput: '',
      allPosts: []
    };
  },
  methods: {
    switchView(val) {
      this.showForm = val;
    },
    addPost() {
      this.allPosts.push({
        author: this.author,
        post: this.postInput
      });
      this.author = '';
      this.postInput = '';
      this.switchView(false);
    }
  },
  components: {
    Post: Post
  }
};
</script>

<style>
</style>