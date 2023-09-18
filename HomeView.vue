<script setup lang="ts">
import { ref } from 'vue'

interface Restaurant {
  name?: string
  status? : RestaurantStatus
  dishes? : Dish[]
}

const ALL_STATUS = ['Want to Try', 'Recommend', 'Must Try']

type RestaurantStatus = typeof ALL_STATUS

const restaurantList = ref<Restaurant[]>([])
const newRestaurant = ref<Restaurant>({})

// How to extract value from type

function addRestaurant() {
  restaurantList.value.push({
    name: newRestaurant.value.name,
    address: '',
    status: 'Want to Try',
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
      <div>
        <label for = "restaurant-name"> Restaurant Name </label>
        <input id = "restaurant-name" v-model = "restaurantName"
               type = "text"
        />
      </div>
      <div>
        <label for = "restaurant-address"> Restaurant Address </label>
        <input id = "restaurant-address" v-model = "restaurantAddress"
               type = "text"
        />
      </div>
      <div>
        <label for = "restaurant-status"> Restaurant Status </label>
        <input id = "restaurant-status" v-model = "restaurantStatus"
               type = "text"
        />
      </div>
        <button type = "submit">Add Restaurant</button>
    </form>
    <ul>
      <li v-for ="restaurant in restaurantList"
          :key="restaurant">
        {{ restaurant.name }}
      </li>
    </ul>
  </main>
</template>
