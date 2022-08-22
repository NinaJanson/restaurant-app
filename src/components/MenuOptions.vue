<template>
  <ul class="menu-list">
    <li class="menu-entry" v-for="menu in Object.entries(diet)" :key="menu[0]">
      <span>{{ menu[0] }}</span>
      <span v-if="menu[1] === true">✔️</span>
      <span v-else>❌</span>
    </li>
  </ul>
</template>

<script>
export default {
  name: "MenuOptions",
  props: {
    diet: Object,
  },
};
</script>

<style scoped>
.menu-list {
  all: unset;
  display: flex;
  flex-direction: column;
  text-align: start;
}

.menu-entry {
  all: unset;
  display: flex;
  flex-direction: row;
  justify-content: start;
  align-items: baseline;
}
</style>
