<template>
  <div>
    <form class="form-content">
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

      <input type="submit" value="ADD" class="btn" />
    </form>
  </div>
</template>

<style scoped>
.form-content {
  display: flex;
  flex-direction: column;
}
.check {
  display: flex;
  justify-content: space-evenly;
  align-items: baseline;
}
.btn {
  display: block;
  width: 100%;
  cursor: pointer;
}
</style>
