<template>
  <div id="app">
    <page/>
  </div>
</template>

<script>
import Page from './components/Page'

export default {
  name: 'app',
  components: {
    'page': Page
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
