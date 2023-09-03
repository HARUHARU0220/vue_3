<script setup lang="ts">
import TheWelcome from '../components/TheWelcome.vue'
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
  </main>
</template>
