<template>
  <div class="form-content">
    <form>
      <div>
        <input type="text" name="text" placeholder="Add Item" />
      </div>
      <div>
        <input type="text" name="cost" placeholder="Cost per Unit" />
      </div>
      <div>
        <input type="number" name="qty" placeholder="Quantity" />
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
  max-width: 400px;
}
input {
  padding: 10px 20px;
  margin-top: 10px;
}
.check {
  display: flex;
  justify-content: space-evenly;
  align-items: baseline;
}
.btn {
  display: block;
  width: 100%;
}
</style>
