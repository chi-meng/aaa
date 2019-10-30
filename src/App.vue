<template>
  <div id="app">

    <HelloWorld/>
    <chen/>
    <shui/>
    <list/>
    <cart/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import chen from './components/chen'
import shui from './components/shui'
import list from "./components/list.vue"
import cart from "./components/cart.vue"
export default {
  name: 'App',
  components: {
    HelloWorld,
    chen,
    shui,
    list,
    cart
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
