<template>
  <div id="app">
    <ViewDatathon/>
  </div>
</template>

<script>
// @ is an alias to /src
import ViewDatathon from '@/views/ViewDatathon.vue'

export default {
  name: 'Home',
  components: {
    ViewDatathon
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

</style>
