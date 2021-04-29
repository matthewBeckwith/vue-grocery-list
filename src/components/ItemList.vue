<template>
  <div v-if="items && items.length > 0">
    <Item :key="item.id" v-for="item in items" :item="item" />
  </div>
  <div v-else>
    <h1 class="themed-text">Add An Item</h1>
  </div>
</template>

<script>
import Item from "./Item";

export default {
  name: "ItemList",
  components: {
    Item,
  },
  props: {
    items: Array,
  },
  emits: ["open-add-item"],
  methods: {
    boom() {
      this.$emit("open-add-item");
    },
  },
};
</script>

<style scoped>
h1 {
  margin-top: 50px;
  text-align: center;
  font-size: clamp(32px, 10vw, 48px);
}
</style>
