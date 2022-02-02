<template>
  <div class="container py-5">
    <div>
      <h1>{{ restaurant.name }}</h1>
      <span class="mt-1 mb-3">
        {{ restaurant.Category.name }}
      </span>
    </div>

    <hr>

    <ul>
      <li>評論數： {{ restaurant.Comments.length }}</li>
      <li>瀏覽次數： {{ restaurant.viewCounts }}</li>
    </ul>

    <button
      type="button"
      class="btn btn-link"
      @click="$router.back()"
    >
      回上一頁
    </button>
  </div>
</template>

<script>
const dummyData = {
  "restaurant": {
    "id": 1,
    "name": "Malinda Ward",
    "tel": "068-332-5988 x7248",
    "address": "319 Morissette Wells",
    "opening_hours": "08:00",
    "description": "Iure facere corporis laboriosam veritatis.",
    "image": "https://loremflickr.com/320/240/restaurant,food/?random=34.26217016006026",
    "viewCounts": 0,
    "createdAt": "2022-01-31T07:49:12.000Z",
    "updatedAt": "2022-01-31T07:49:12.000Z",
    "CategoryId": 2,
    "Category": {
      "id": 2,
      "name": "日本料理",
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z"
    },
    "Comments": [
      {
        "id": 101,
        "text": "Aut quas ut totam.",
        "UserId": 1,
        "RestaurantId": 1,
        "createdAt": "2022-01-31T07:49:12.000Z",
        "updatedAt": "2022-01-31T07:49:12.000Z",
        "User": {
          "id": 1,
          "name": "root",
          "email": "root@example.com",
          "password": "$2a$10$lhQQRzd.MiI7bFp/Hnwx8upe8.6gEX7a6bsRKwgLC88on0M3UiR9a",
          "isAdmin": true,
          "image": null,
          "createdAt": "2022-01-31T07:49:12.000Z",
          "updatedAt": "2022-01-31T07:49:12.000Z"
        }
      },
      {
        "id": 51,
        "text": "Sed quia qui voluptas veniam quibusdam libero ipsum quo est.",
        "UserId": 2,
        "RestaurantId": 1,
        "createdAt": "2022-01-31T07:49:12.000Z",
        "updatedAt": "2022-01-31T07:49:12.000Z",
        "User": {
          "id": 2,
          "name": "user1",
          "email": "user1@example.com",
          "password": "$2a$10$hiu0H/XQNx/AFiPmiBJA7uc7IBHMYmbrNWQGlvr.nNFmA8IU.ljdW",
          "isAdmin": false,
          "image": null,
          "createdAt": "2022-01-31T07:49:12.000Z",
          "updatedAt": "2022-01-31T07:49:12.000Z"
        }
      },
      {
        "id": 1,
        "text": "Voluptas sint dolores omnis cum.",
        "UserId": 3,
        "RestaurantId": 1,
        "createdAt": "2022-01-31T07:49:12.000Z",
        "updatedAt": "2022-01-31T07:49:12.000Z",
        "User": {
          "id": 3,
          "name": "user2",
          "email": "user2@example.com",
          "password": "$2a$10$oeZAkhtCQTk/KQ2N4pkp..S93mPXWZ3bngAOyJDo70V.TSs3YMXCS",
          "isAdmin": false,
          "image": null,
          "createdAt": "2022-01-31T07:49:12.000Z",
          "updatedAt": "2022-01-31T07:49:12.000Z"
        }
      }
    ]
  }
}

export default {
  data() {
    return {
      restaurant: ''
    }
  },
  created() {
    const { id: restaurantId } = this.$route.params
    this.fetchRestaurant(restaurantId)
  },
  methods: {
    fetchRestaurant(restaurantId) {
      console.log('restaurantId: ', restaurantId)
      this.restaurant = dummyData.restaurant
    }
  }
}
</script>
