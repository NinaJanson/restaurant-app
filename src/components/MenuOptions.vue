<template>
  <ul>
    <li v-for="menu in Object.entries(diet)" :key="menu[0]">
      {{ menu[0] }}
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
