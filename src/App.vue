<template>
  <div id="app">
    <create-post></create-post>
    <get-post></get-post>
   
  </div>
</template>

<script>
import CreatePost from './components/CreatePost.vue'
import GetPost from './components/GetPost.vue'
export default {
  name: 'App',
  components: {
    CreatePost,
    GetPost
  },
 
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
