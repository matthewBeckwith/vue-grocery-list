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
      items: [
        {
          id: 1,
          text: "Milk",
          cost: "3.54",
          qty: 1,
          disc: false,
        },
        {
          id: 2,
          text: "Bread",
          cost: "1.25",
          qty: 2,
          disc: false,
        },
        {
          id: 3,
          text: "Razors",
          cost: "8.50",
          qty: 1,
          disc: true,
        },
        {
          id: 4,
          text: "Cucumber",
          cost: "0.50",
          qty: 3,
          disc: false,
        },
      ],
    };
  },
  methods: {
    openAddItem() {
      this.showAddItem = true;
    },
    closeAddItem() {
      this.show = false;
    },
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
