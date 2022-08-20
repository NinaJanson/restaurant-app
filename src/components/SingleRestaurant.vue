<template>
  <ul>
    <li>
      <p>{{ restaurantName }}</p>
      <StarList :rating="rating" />
      <MenuOptions :diet="diet" />
      <IconButton @clicked="clickHandler" :buttonContent="toggleHeart" />
      <IconButton @clicked="toggleModal" :buttonContent="'🌍'" />
      <ModalAddress v-if="modalActive" @closeModal="toggleModal">
        <address>
          {{ restaurantName }} <br />
          {{ streetAddress }} <br />
          {{ city }}
        </address>
      </ModalAddress>
    </li>
  </ul>
</template>

<script>
import IconButton from "@/components/IconButton.vue";
import MenuOptions from "@/components/MenuOptions.vue";
import StarList from "@/components/StarList.vue";
import ModalAddress from "@/components/ModalAddress.vue";
import { ref } from "vue";

export default {
  name: "SingleRestaurant",
  emits: ["marked"],
  props: {
    restaurantName: String,
    isMarkedAsFavorite: Boolean,
    id: Number,
    rating: Number,
    diet: Object,
    streetAddress: String,
    city: String,
  },
  components: {
    IconButton,
    StarList,
    MenuOptions,
    ModalAddress,
  },
  setup() {
    const modalActive = ref(false);

    const toggleModal = () => {
      modalActive.value = !modalActive.value;
    };

    return {
      modalActive,
      toggleModal,
    };
  },

  computed: {
    toggleHeart() {
      return this.isMarkedAsFavorite ? "💙" : "🤍";
    },
  },
  methods: {
    clickHandler() {
      this.$emit("marked", this.id);
    },
  },
};
</script>

<style scoped>
li {
  border: black solid 2px;
}
</style>
