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

interface Restaurant {
  name?: string
  address? : string
  status? : string
  dishes? : Dish[]
}

const restaurantList = ref<Restaurant[]>([])
const newRestaurant = ref<Restaurant>({})

function addRestaurant() {
  restaurantList.value.push({
    name: newRestaurantName.value,
    address: '',
    status: '',
    dishes: []
  })
}

</script>

<template>
  <main>
    <pre>
      {{ newRestaurant }}
    </pre>
    <!---create a from that allows users to add a restaurant to a list-->
    <form @submit.prevent = "addRestaurant">
      <label for = "restaurant-name"> Restaurant Name </label>
      <input id = "restaurant-name" v-model = "restaurantName"
             type = "text" />
      <button type = "submit">Add Restaurant</button>
    </form>
    <ul>
      <li v-for ="restaurant in restaurantList"
          : key="restaurant">
        {{ restaurant.name }}
      </li>
    </ul>
  </main>
</template>
