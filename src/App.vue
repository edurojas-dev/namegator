<template>
  <div id="app">
    <home/>
  </div>
</template>

<script>
import home from "./pages/home"
export default {
  name: 'App',
  components: {
    home,
  }
}
</script>

<style scoped>
body{
  margin: 0;
  padding: 0;
}
</style>
