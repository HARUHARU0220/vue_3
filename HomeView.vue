<script setup lang="ts">

import { ref } from 'vue'

/**
 * Restaurants
 *
 * Name - string
 * Status - string
 * Address - string
 * Dishes - array of Dish objects
 *
 */


const restaurantList = ref<string[]>([]);
const newRestaurantName = ref('')

function addRestaurant() {
  restaurantList.value.push(newRestaurantName.value)

}

</script>

<template>
  <main>
    <!---create a from that allows users to add a restaurant to a list-->
    <form @submit.prevent = "addRestaurant">
      <label for = "restaurant-name"> Restaurant Name </label>
      <input id = "restaurant-name" v-model = "restaurantName"
             type = "text" />
      <button type = "submit">Add Restaurant</button>
    </form>
    <ul>
      <li v-for ="restaurant in restaurantList" key="restaurant">
        {{ restaurant }}
      </li>
    </ul>
  </main>
</template>
