<template>
  <div class="container py-5">
    <NavTabs />
    <h1 class="mt-5">
      人氣餐廳
    </h1>

    <hr>
    <RestaurantsTopCard
      v-for="restaurant in restaurants"
      :key="restaurant.id"
      :initial-restaurant="restaurant"
    />
  </div>
</template>

<script>
import NavTabs from '../components/NavTabs.vue'
import RestaurantsTopCard from '../components/RestaurantTopCard.vue'
import restaurantsAPI from '../apis/restaurants'
import { Toast } from '../utils/helpers'

export default {
  components: {
    NavTabs,
    RestaurantsTopCard
  },
  data() {
    return {
      restaurants: ''
    }
  },
  created() {
    this.fetchRestaurants()
  },
  methods: {
    async fetchRestaurants() {
      try {
        const { data } = await restaurantsAPI.getTop()

        this.restaurants = data.restaurants
      }
      catch (error) {
        Toast.fire({
          icon: 'error',
          title: '無法取得人氣餐廳資料，請稍後再試'
        })
      }
    }
  }
}
</script>