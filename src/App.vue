<template>
<div id="app">
  <p>{{msg}}</p>
      <p>React tutorial done in Vue.js. Code on <a href="https://github.com/mconnor/vue-tac-toe">github</a></p>
<div class='myrow'>
      <game></game>
      <game></game></div>
</div>
</template>

<script>
import Game from './components/Game.vue'

export default {
  name: 'app',
  components: {
    Game,
  },
  data() {
    return {
      msg: '<game></game> gets you one game of tic-tac-toe',
    };
  },
};
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
.myrow {
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  justify-content: space-around;
}
</style>
