<template>
  <button @click="$emit('clicked')">{{ buttonContent }}</button>
</template>

<script>
export default {
  name: "IconButton",
  emits: ["clicked"],
  props: {
    buttonContent: String,
  },
};
</script>

<style scoped>
button {
  all: unset;
  border: rgb(0, 81, 255) solid 2px;
  border-radius: 5px;
  margin: 0.25rem;
  height: 2rem;
  width: 2rem;
  font-size: 1.25rem;
  background-color: rgb(89, 163, 243);
}
</style>
