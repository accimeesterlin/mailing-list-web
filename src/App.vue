<template>
  <div id="app">
    <Home />
  </div>
</template>

<script>
import Home from './views/Home.vue';

export default {
  components: {
    Home,
  },
};
</script>


<style>
  #app {
    width: 100%;
    background-color: #b2d3be;
    height: 100vh;
  }

  h1 {
    font-size: 45px;
    font-family: sans-serif;
    font-weight: bold;
    line-height: 1;
    color: #111;
    letter-spacing: -1px;
  }

  h2 {
    font-size: 30px;
    font-weight: 300;
    font-family: sans-serif;
    line-height: 32px;
  }
  p {
    font-family: sans-serif;
  }
</style>
