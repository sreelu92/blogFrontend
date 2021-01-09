<template>
  <div>
    <h2>Update Post</h2>
    <h3>Name</h3>
    <input v-model="postName" type="text" />
    <h2>Content</h2>
    <input v-model="postContent" type="text" />
    <h2>Created Date</h2>
    <input v-model="postCreate" type="text" />
    <button @click="updatePost">Update</button>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: "update-post",
  data() {
    return {
      postName: "",
      postContent: "",
      postCreate: "",
    };
  },
  props: {
    postid: {
      type: Number,
      required: true,
    },
  },
  methods: {
    updatePost: function () {
      axios
        .request({
          url: "http://blogspost.ml/api/post",
          method: "PATCH",
          headers: {
            "Content-Type": "application/json",
          },
          data: {
            name: this.postName,
            content: this.postContent,
            created: this.postCreate,
            id:this.postid
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