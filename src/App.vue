<template>
  <div id="app">
    <Nav title="Grocery List" />
    <router-view />
  </div>
</template>

<script>
import Nav from "./components/Nav";

export default {
  components: {
    Nav,
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
