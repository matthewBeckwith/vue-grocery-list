<template>
  <div class="main-content">
    <AddItem class="col" />
    <ItemList class="col-wide" :items="items" @open-add-item="openAddItem" />
  </div>
</template>

<script>
import AddItem from "../components/AddItem";
import ItemList from "../components/ItemList";

export default {
  name: "Home",
  components: {
    AddItem,
    ItemList,
  },
  data() {
    return {
      showAddItem: false,
      items: [],
    };
  },
  methods: {
    // -- Show / Hide Form
    openAddItem() {
      this.showAddItem = true;
    },
    closeAddItem() {
      this.show = false;
    },

    // - Get ALL Items
    async fetchItems() {
      const res = await fetch("api/items");
      const data = await res.json();

      return data;
    },

    // - Get a Specific Item
    async fetchItem(id) {
      const res = await fetch(`api/items/${id}`);
      const data = await res.json();

      return data;
    },
  },

  // - On Create
  async created() {
    this.items = await this.fetchItems();
  },
};
</script>

<style scoped>
.main-content {
  padding: 30px;
}
.col-wide {
  margin-top: 10px;
}
</style>
