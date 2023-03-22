<template>
  <div id="app">
    <img class="page-image" alt="Vue logo" src="https://www.pngmart.com/files/21/Administration-Download-PNG-Image.png">
    <Management msg="Management of analytics file data"/>
  </div>
</template>

<script>
import Management from './components/Management.vue'

export default {
  name: 'App',
  components: {
    Management
  }
}
</script>

<style>
.page-image {
  width: auto;
  height: 200px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
