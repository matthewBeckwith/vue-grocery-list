<template>
  <div :class="[item.disc ? 'item-container disc' : 'item-container']">
    <small class="row">
      <div class="left-col">
        <span
          ><i
            @click="$emit('decrease-qty', item.id)"
            class="fas fa-chevron-left"
          ></i
        ></span>
        <span>{{ item.qty }}</span>
        <span
          ><i
            @click="$emit('increase-qty', item.id)"
            class="fas fa-chevron-right"
          ></i
        ></span>
      </div>
      <div class="center-col" @dblclick="$emit('toggle-discount', item.id)">
        <span>{{ item.text }}</span>
      </div>
      <div class="right-col">
        <span>{{ item.total }}</span>
        <span
          ><i @click="$emit('delete-item', item.id)" class="fas fa-times"></i
        ></span>
      </div>
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
}
.disc {
  border: 1px solid #42b883;
  border-left: 5px solid #42b883;
}
.row {
  display: flex;
  justify-content: space-between;
  width: 100%;
  padding: 10px 20px;
  align-items: center;
}
.left-col {
  width: 15%;
  display: flex;
  justify-content: space-between;
}
.center-col {
  width: 60%;
  display: flex;
  justify-content: flex-start;
  cursor: pointer;
}
.right-col {
  padding-right: 20px;
}
.fas {
  cursor: pointer;
}
.fa-times {
  padding-left: 20px;
  color: #850d0d;
}
</style>
