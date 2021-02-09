<template>
  <div id="app">
    <header>
      <nav>
        <ul>
          <li class="nav-item">
            <img class="logo" src="./assets/build-a-bot-logo.png">
            Build-a-Bot
          </li>
        </ul>
      </nav>
    </header>
    <main>
      <home-page />
      <robot-builder />
    </main>
    <img alt="Vue logo" src="./assets/logo.png">
    <MiniComponent msg="a passed in msg" />
    <mini-component msg="also working?!" />
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import RobotBuilder from './builder/RobotBuilder.vue';
import HelloWorld from './components/HelloWorld.vue';
import HomePage from './components/HomePage.vue';
import MiniComponent from './components/MiniComponent.vue';

export default {
  name: 'App',
  components: {
    HelloWorld,
    MiniComponent,
    HomePage,
    RobotBuilder,
  },
};
</script>

<style>
body {
  background: linear-gradient(to bottom, #555, #999);
  background-attachment: fixed;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
main {
  margin: 0 auto;
  padding: 30px;
  background-color: white;
  width: 1024px;
  min-height: 300px;
}
header {
  background-color: #999;
  width: 1084px;
  margin: 0 auto;
}
ul {
  padding: 3px;
  display: flex;
}
.nav-item {
  display: inline-block;
  padding: 5px 10px;
  font-size: 22px;
  border-right: 1px solid #bbb;
}
.logo {
  vertical-align: middle;
  height: 30px;
}
</style>
