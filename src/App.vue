<template>
  <div>
    <Nav title="Grocery List" />
    <router-view class="app-layout" />
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
@import url("https://fonts.googleapis.com/css2?family=Lobster&family=Oswald:wght@200&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Oswald:wght@200&display=swap");

h1,
h2,
h3,
h4,
h5,
h6 {
  font-family: "Lobster", cursive;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: "Oswald", sans-serif;
}

input {
  font-family: "Oswald", sans-serif;
}
input:not([type="checkbox"]) {
  padding: 10px 20px;
  margin-top: 10px;
  width: 100%;
  border: dashed #ccc;
  border-radius: 8px;
}
input:focus {
  outline: none;
}

input[type="checkbox"] {
  background-color: #ddd;
  border-radius: 10px;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  width: 17px;
  height: 17px;
  cursor: pointer;
  position: relative;
  top: 5px;
}

input[type="checkbox"]:checked {
  background-color: #42b883;
  background: #42b883
    url("data:image/gif;base64,R0lGODlhCwAKAIABAP////3cnSH5BAEKAAEALAAAAAALAAoAAAIUjH+AC73WHIsw0UCjglraO20PNhYAOw==")
    3px 3px no-repeat;
}

.col {
  flex-shrink: 2;
  min-width: 200px;
  max-width: 500px;
}

.col-wide {
  flex-shrink: 2;
  min-width: 200px;
  max-width: 800px;
  width: 100%;
}

.themed-text {
  color: #42b883;
  text-shadow: rgba(204, 204, 204, 0.4) 2px 3px;
}

@media (min-width: 500px) {
  .app-layout {
    display: flex;
    justify-content: space-around;
    margin: 30px auto;
    max-width: 70vw;
    gap: 30px;
  }
}
</style>
