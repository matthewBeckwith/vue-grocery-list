<template>
  <div>
    <div v-if="showAddItemForm">
      <form @submit="submitAddItemForm" class="form-content">
        <div>
          <input
            autocomplete="off"
            type="text"
            name="text"
            placeholder="Add Item"
          />
        </div>
        <div>
          <input
            autocomplete="off"
            type="text"
            name="cost"
            placeholder="Cost per Unit"
          />
        </div>
        <div>
          <input
            autocomplete="off"
            type="number"
            name="qty"
            min="1"
            max="10"
            placeholder="Quantity"
          />
        </div>
        <div class="check">
          <label>Coupon?</label>
          <input type="checkbox" name="coupon" />
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
import Button from "./Button";

export default {
  name: "AddItem",
  components: {
    Button,
  },
  data() {
    return {
      showAddItemForm: false,
    };
  },
  methods: {
    submitAddItemForm(e) {
      e.preventDefault();

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
</style>
