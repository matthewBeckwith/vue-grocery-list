<template>
  <div>
    <div>
      <h3>{{ title }}</h3>
    </div>
    <div class="links">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "Nav",
  props: {
    title: String,
  },
};
</script>

<style scoped>
div {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 5px 10px;
}

.links {
  display: flex;
  justify-content: space-evenly;
  width: 30%;
}

a {
  font-weight: bold;
  color: #2c3e50;
  text-decoration: none;
}

a.router-link-exact-active {
  color: #42b983;
}
</style>
