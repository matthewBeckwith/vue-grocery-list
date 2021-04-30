<template>
  <div v-if="items && items.length > 0">
    <Item
      v-for="item in items"
      :key="item.id"
      :item="item"
      @toggle-discount="$emit('toggle-discount', item.id)"
      @increase-qty="$emit('increase-qty', item.id)"
      @decrease-qty="$emit('decrease-qty', item.id)"
      @delete-item="$emit('delete-item', item.id)"
    />
  </div>
  <div v-else>
    <h1 class="themed-text">Add An Item</h1>
  </div>
</template>

<script>
import Item from "./Item";

export default {
  name: "ItemList",
  props: {
    items: Array,
  },
  components: {
    Item,
  },
  emits: ["toggle-discount", "delete-item", "increase-qty", "decrease-qty"],
};
</script>

<style scoped>
h1 {
  margin-top: 50px;
  text-align: center;
  font-size: clamp(32px, 10vw, 48px);
}
</style>
