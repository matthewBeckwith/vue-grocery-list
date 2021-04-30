<template>
  <div class="main-content">
    <AddItem @add-item="addItem" class="col" />
    <ItemList
      @toggle-discount="toggleDiscount"
      @increase-qty="increaseQty"
      @decrease-qty="decreaseQty"
      @delete-item="deleteItem"
      class="col-wide"
      :items="items"
    />
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

    // - Add an Item
    async addItem(item) {
      const res = await fetch("api/items", {
        method: "POST",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(item),
      });

      const data = await res.json();

      this.items = [...this.items, data];
    },

    // - Update an Item
    async toggleDiscount(id) {
      const thisItem = await this.fetchItem(id);
      const updatedItem = { ...thisItem, disc: !thisItem.disc };

      const res = await fetch(`api/items/${id}`, {
        method: "PUT",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(updatedItem),
      });

      const data = await res.json();

      this.items = this.items.map((item) =>
        item.id === id ? { ...item, disc: data.disc } : item
      );
    },

    // - Increase the Quantity
    async increaseQty(id) {
      const thisItem = await this.fetchItem(id);
      const newQty = thisItem.qty + 1;
      const newTotal = thisItem.cost * newQty;
      const updatedItem = { ...thisItem, qty: newQty, total: newTotal };

      const res = await fetch(`api/items/${id}`, {
        method: "PUT",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(updatedItem),
      });

      const data = await res.json();

      this.items = this.items.map((item) =>
        item.id === id ? { ...item, qty: data.qty, total: data.total } : item
      );
    },

    // - Decrease the Quantity
    async decreaseQty(id) {
      const thisItem = await this.fetchItem(id);
      const newQty = thisItem.qty - 1;
      const newTotal = thisItem.cost * newQty;
      const updatedItem = { ...thisItem, qty: newQty, total: newTotal };

      const res = await fetch(`api/items/${id}`, {
        method: "PUT",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(updatedItem),
      });

      const data = await res.json();

      this.items = this.items.map((item) =>
        item.id === id ? { ...item, qty: data.qty, total: data.total } : item
      );
    },

    // - Delete an Item
    async deleteItem(id) {
      const res = await fetch(`api/items/${id}`, {
        method: "DELETE",
      });

      res.status === 200
        ? (this.items = this.items.filter((item) => item.id !== id))
        : alert("Delete ITEM Error");
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
