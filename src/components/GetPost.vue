<template>
  <div>
    <button @click="getPosts">Get Posts</button>

    <div v-for="post in posts" :key="post[3]">
      <h4>{{ "Name: " + post[0] }}</h4>
      <h4>{{ "Content: " + post[1] }}</h4>
      <h4>{{ "Created at: " + post[2] }}</h4>
      <update-post :postid="post[3]"></update-post>
      <delete-post :postid="post[3]"></delete-post>
    </div>
  </div>
</template>

<script>
import axios from "axios"
import UpdatePost from "./UpdatePost.vue";
import DeletePost from "./DeletePost.vue";
export default {
  name: "get-post",
  components: {
    UpdatePost,
    DeletePost,
  },
  data() {
    return {
      posts: [],
    };
  },
  methods: {
    getPosts: function () {
      axios
        .request({
          url: "http://blogspost.ml/api/blogpost",
          method: "GET",
        })
        .then((response) => {
          console.log(response);
          this.posts = response.data;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style scoped>
</style>