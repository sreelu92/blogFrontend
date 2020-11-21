<template>
  <div>
    <h2>Create Post</h2>
    <h3>Name</h3>
    <input v-model="postName" type="text" />
    <h2>Content</h2>
    <input v-model="postContent" type="text" />
    <h2>Created Date</h2>
    <input v-model="postCreate" type="text" />
    <button @click="createPost">Post</button>
  </div>
</template>

<script>
import axios from'axios'
export default {
  name: "create-post",
  data() {
    return {
      postName: "",
      postContent: "",
      postCreate: "",
    };
  },
  methods: {
    createPost: function () {
      axios
        .request({
          url: "http://blogspost.ml/api/blogpost",
          method: "POST",
          headers: {
            "Content-Type": "application/json",
          },
          data: {
            name: this.postName,
            content: this.postContent,
            created: this.postCreate,
          },
        })
        .then((response) => {
          console.log(response);
        })
        .catch((error) => {
          console.log(error);
        });
    }
  }
};
</script>

<style scoped>
</style>