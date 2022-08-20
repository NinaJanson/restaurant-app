<template>
  <div class="home">
    <SingleRestaurant
      v-for="restaurant in visibleRestaurants"
      :key="restaurant.id"
      :restaurantName="restaurant.name"
      :id="restaurant.id"
      @marked="toggleFavoriteButton"
      :isMarkedAsFavorite="restaurant?.isMarkedAsFavorite"
      :rating="restaurant.rating"
      :diet="restaurant.diet"
      :city="restaurant.address.city"
      :streetAddress="restaurant.address.streetAddress"
    />
  </div>
  <button
    @click="loadRestaurants += loadMoreRestaurants"
    v-show="loadRestaurants <= restaurants.length"
  >
    more
  </button>
</template>

<script>
// @ is an alias to /src
import SingleRestaurant from "@/components/SingleRestaurant.vue";

export default {
  name: "HomeView",
  components: {
    SingleRestaurant,
  },

  data() {
    return {
      restaurants: [],
      loadRestaurants: 3,
      loadMoreRestaurants: 3,
    };
  },

  async mounted() {
    const response = await fetch("http://localhost:3000/restaurants");
    this.restaurants = await response.json();
  },

  computed: {
    visibleRestaurants() {
      return this.restaurants.slice(0, this.loadRestaurants);
    },
  },

  methods: {
    toggleFavoriteButton(id) {
      const favoriteRestaurantId = this.restaurants.findIndex(
        (restaurant) => restaurant.id === id
      );
      this.restaurants[favoriteRestaurantId].isMarkedAsFavorite =
        !this.restaurants[favoriteRestaurantId].isMarkedAsFavorite;
    },
  },
};
</script>
