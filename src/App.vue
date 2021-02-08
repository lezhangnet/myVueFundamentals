<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <MiniComponent msg="a passed in msg" />
    <mini-component msg="also working?!" />
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import MiniComponent from './components/MiniComponent.vue';

export default {
  name: 'App',
  components: {
    HelloWorld,
    MiniComponent,
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
