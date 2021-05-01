<template>
  <div>
    <h1 class="total_txt">{{ total }}</h1>
    <div v-if="showAddItemForm">
      <form @submit="submitAddItemForm" class="form-content">
        <div>
          <input
            autocomplete="off"
            type="text"
            name="text"
            v-model="newItem.text"
            placeholder="Add Item"
          />
        </div>
        <div>
          <input
            autocomplete="off"
            type="text"
            name="cost"
            v-model="newItem.cost"
            placeholder="Cost per Unit"
          />
        </div>
        <div>
          <input
            autocomplete="off"
            type="number"
            name="qty"
            v-model="newItem.qty"
            min="1"
            max="10"
            placeholder="Quantity"
          />
        </div>
        <div class="check">
          <label>Coupon?</label>
          <input type="checkbox" name="coupon" v-model="newItem.disc" />
        </div>

        <Button type="submit" text="ADD" />
      </form>
    </div>
    <div>
      <Button
        @btn-clicked="showAddItemForm = true"
        v-if="!showAddItemForm"
        type="button"
        text="ADD"
      />
    </div>
  </div>
</template>

<script>
import ID from "simple-random-string-creator";
import Button from "./Button";

export default {
  name: "AddItem",
  props: {
    total: String,
  },
  components: {
    Button,
  },
  data() {
    return {
      showAddItemForm: false,
      newItem: {
        text: "",
        cost: "",
        qty: "",
        disc: false,
      },
    };
  },
  methods: {
    submitAddItemForm(e) {
      e.preventDefault();

      if (!this.newItem.text || !this.newItem.cost) {
        alert(
          "The form is incomplete; Please fill out the form to submit an item to the list.  By default the 'Quantity' is set to 1"
        );
        return;
      }

      const cost = parseFloat(this.newItem.cost);
      const qty = this.newItem.qty ? parseInt(this.newItem.qty) : 1;
      const total = cost * qty;

      const newItem = {
        id: ID(),
        text: this.newItem.text,
        cost,
        qty,
        total: total.toFixed(2),
        disc: this.newItem.disc,
      };
      console.log(newItem);
      this.$emit("add-item", newItem);

      this.newItem.text = "";
      this.newItem.cost = "";
      this.newItem.qty = "";
      this.newItem.disc = false;

      this.showAddItemForm = false;
    },
  },
};
</script>

<style scoped>
.form-content {
  display: flex;
  flex-direction: column;
}
.check {
  display: flex;
  justify-content: space-evenly;
  align-items: baseline;
  padding: 15px 0 5px 0;
}
.btn {
  display: block;
  width: 100%;
  cursor: pointer;
}
.total_txt {
  text-align: center;
  color: #999;
}
</style>
