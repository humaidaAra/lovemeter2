<template>
  <div class="container">
    <cont />
    <resultpane />
   
  </div>
</template>

<script>

import cont from './components/cont.vue'
import resultpane from './components/resultpane.vue'

export default 
{
  name: 'App',
  components: 
  {
    cont,
    resultpane
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 10px;
  height: 100%;
}
html,body
{
  height: 100%;
  width: 100%;
}
</style>
