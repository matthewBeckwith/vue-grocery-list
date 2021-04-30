<template>
  <div :class="[item.disc ? 'item-container disc' : 'item-container']">
    <small class="row">
      <div class="left-col">
        <span>{{ item.qty }}</span>
        <span>{{ item.text }}</span>
      </div>
      <span class="right-col">{{ item.total }}</span>
    </small>
  </div>
</template>

<script>
export default {
  name: "Item",
  props: {
    item: Object,
  },
};
</script>

<style scoped>
.item-container {
  width: 100%;
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-bottom: 5px;
  cursor: pointer;
}
.disc {
  border: 1px solid #42b883;
  border-left: 5px solid #42b883;
}
.row {
  display: flex;
  justify-content: space-between;
  width: 100%;
  height: 30px;
  align-items: center;
}
.left-col {
  display: flex;
  justify-content: space-evenly;
}
.left-col > span {
  padding-left: 20px;
}
.right-col {
  padding-right: 20px;
}
</style>
