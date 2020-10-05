<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">    
    <HelloWorld :idactivity="id" :titulo="portada1" :tipo="tipo1" :cantidad="2"></HelloWorld>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data() {
    return {
      id : 13,
      portada1 : 'Titulo',
      tipo1 : 1,
    }
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
