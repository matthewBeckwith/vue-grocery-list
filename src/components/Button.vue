<template>
  <input @click="clicked()" :type="type" :value="text" class="btn" />
</template>

<script>
export default {
  name: "Button",
  props: {
    type: String,
    text: String,
  },
  methods: {
    clicked() {
      this.$emit("btn-clicked");
    },
  },
};
</script>
