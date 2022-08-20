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
