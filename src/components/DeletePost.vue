<template>
  <div>
    <button @click="deletePost">Delete Post</button>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: "delete-post",
  props: {
    postid: {
      type: Number,
      required: true,
    },
  },
  methods: {
    deletePost: function () {
      axios
        .request({
          url: "http://blogspost.ml/api/post",
          method: "DELETE",
          headers: {
            "Content-Type": "application/json",
          },
          data: {
            id: this.postid,
          },
        })
        .then((response) => {
          console.log(response);
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