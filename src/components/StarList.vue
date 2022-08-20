<template>
  <div class="stars">
    <span>&#9734;</span><span>&#9734;</span><span>&#9734;</span
    ><span>&#9734;</span><span>&#9734;</span>
    <div class="stars-filled" :style="{ width: rating * 20 + '%' }">
      <span>&starf;</span>
      <span>&starf;</span>
      <span>&starf;</span>
      <span>&starf;</span>
      <span>&starf;</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "StarList",
  props: {
    rating: Number,
  },
};
</script>

<style scoped>
.stars {
  position: relative;
  display: inline-block;
  color: yellow;
  font-size: 2rem;
}

.stars-filled {
  position: absolute;
  top: 0;
  overflow: hidden;
}
</style>
