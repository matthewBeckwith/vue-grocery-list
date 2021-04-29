<template>
  <div class="main-content">
    <AddItem />
    <h3>List of items</h3>
  </div>
</template>

<script>
import AddItem from "../components/AddItem";

export default {
  name: "Home",
  components: {
    AddItem,
  },
};
</script>

<style scoped>
.main-content {
  display: flex;
  justify-content: space-between;
  max-width: 95%;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
</style>
