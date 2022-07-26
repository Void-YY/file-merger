<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <FileSelector />
</template>

<script>
import FileSelector from "./components/FileSelector.vue";

export default {
  name: "App",
  components: {
    FileSelector,
  },
};
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
