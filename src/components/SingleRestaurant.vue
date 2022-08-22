<template>
  <ul>
    <li class="list">
      <p class="restaurant-name">{{ restaurantName }}</p>

      <StarList :rating="rating" />
      <MenuOptions :diet="diet" />
      <div class="button-container">
        <IconButton @clicked="clickHandler" :buttonContent="toggleHeart" />
        <IconButton @clicked="toggleModal" :buttonContent="'🌍'" />
      </div>
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
ul {
  all: unset;
}
.list {
  border: black solid 2px;
  display: grid;
  grid-template-columns: 2fr 2fr 1fr;
  grid-template-rows: auto 1fr;
  padding: 0.5rem;
  margin: 1rem;
}

.restaurant-name {
  grid-column-start: span 4;
  text-align: start;
  font-weight: bold;
}

.button-container {
  display: flex;
  flex-direction: column;
  margin: 0.5rem;
}
</style>
