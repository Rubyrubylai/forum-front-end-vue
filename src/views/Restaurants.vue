<template>
  <div class="container py-5">
    <NavTabs />
    <RestaurantsNavPills 
      :categories="categories"
    />

    <div class="row">
      <RestaurantCard
        v-for="restaurant in restaurants"
        :key="restaurant.id"
        :initial-restaurant="restaurant"
      />
    </div>

    <RestaurantsPagination 
      v-if="totalPage.length > 1"
      :current-page="currentPage"
      :total-page="totalPage"
      :category-id="CategoryId"
      :previous-page="previousPage"
      :next-page="nextPage"
    />

  </div>
</template>

<script>
import NavTabs from '../components/NavTabs.vue'
import RestaurantCard from '../components/RestaurantCard.vue'
import RestaurantsNavPills from '../components/RestaurantsNavPills.vue'
import RestaurantsPagination from '../components/RestaurantsPagination.vue'

const dummyData = {
  "restaurants": [
    {
      "id": 19,
      "name": "Francisca Kohler",
      "tel": "(740) 553-2109",
      "address": "915 Cormier Walks",
      "opening_hours": "08:00",
      "description": "Soluta quos voluptatem qui.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=7.906401984053835",
      "viewCounts": 0,
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z",
      "CategoryId": 1,
      "Category": {
          "id": 1,
          "name": "中式料理",
          "createdAt": "2022-01-31T07:49:12.000Z",
          "updatedAt": "2022-01-31T07:49:12.000Z"
      },
      "isFavorited": false,
      "isLiked": false
    },
    {
      "id": 20,
      "name": "Asa Ortiz",
      "tel": "724.501.1498 x3419",
      "address": "70918 Hoeger Cape",
      "opening_hours": "08:00",
      "description": "Recusandae distinctio nostrum deserunt ea voluptat",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=28.213601656299268",
      "viewCounts": 0,
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z",
      "CategoryId": 1,
      "Category": {
          "id": 1,
          "name": "中式料理",
          "createdAt": "2022-01-31T07:49:12.000Z",
          "updatedAt": "2022-01-31T07:49:12.000Z"
      },
      "isFavorited": false,
      "isLiked": false
    },
    {
      "id": 23,
      "name": "Damon Nicolas",
      "tel": "(819) 464-9257 x3067",
      "address": "9667 Madison Underpass",
      "opening_hours": "08:00",
      "description": "Itaque harum dolores doloremque consequatur aliqui",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=40.027755954732136",
      "viewCounts": 0,
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z",
      "CategoryId": 1,
      "Category": {
          "id": 1,
          "name": "中式料理",
          "createdAt": "2022-01-31T07:49:12.000Z",
          "updatedAt": "2022-01-31T07:49:12.000Z"
      },
      "isFavorited": false,
      "isLiked": false
    },
    {
      "id": 24,
      "name": "Mertie Wunsch",
      "tel": "737.019.8466 x34285",
      "address": "39119 Wilson Orchard",
      "opening_hours": "08:00",
      "description": "Ut quo animi voluptate qui. Qui molestiae beatae d",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=34.56423405565807",
      "viewCounts": 0,
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z",
      "CategoryId": 1,
      "Category": {
          "id": 1,
          "name": "中式料理",
          "createdAt": "2022-01-31T07:49:12.000Z",
          "updatedAt": "2022-01-31T07:49:12.000Z"
      },
      "isFavorited": false,
      "isLiked": false
    },
    {
      "id": 25,
      "name": "Braeden Pfeffer",
      "tel": "364.600.8103 x576",
      "address": "051 Hansen Shores",
      "opening_hours": "08:00",
      "description": "Officia molestiae id molestiae quaerat maxime sint",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=58.749423656025535",
      "viewCounts": 0,
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z",
      "CategoryId": 1,
      "Category": {
          "id": 1,
          "name": "中式料理",
          "createdAt": "2022-01-31T07:49:12.000Z",
          "updatedAt": "2022-01-31T07:49:12.000Z"
      },
      "isFavorited": false,
      "isLiked": false
    },
    {
      "id": 38,
      "name": "Miss Lowell Cartwright",
      "tel": "1-547-151-9912",
      "address": "8071 Mia Corner",
      "opening_hours": "08:00",
      "description": "Id laboriosam et repellendus voluptatum amet sit. ",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=81.33209937017763",
      "viewCounts": 0,
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z",
      "CategoryId": 1,
      "Category": {
          "id": 1,
          "name": "中式料理",
          "createdAt": "2022-01-31T07:49:12.000Z",
          "updatedAt": "2022-01-31T07:49:12.000Z"
      },
      "isFavorited": false,
      "isLiked": false
    },
    {
      "id": 48,
      "name": "Eda Crist",
      "tel": "375-354-8129 x17211",
      "address": "80611 Bernhard Mews",
      "opening_hours": "08:00",
      "description": "animi rerum repudiandae",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=64.404766436467",
      "viewCounts": 0,
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z",
      "CategoryId": 1,
      "Category": {
          "id": 1,
          "name": "中式料理",
          "createdAt": "2022-01-31T07:49:12.000Z",
          "updatedAt": "2022-01-31T07:49:12.000Z"
      },
      "isFavorited": false,
      "isLiked": false
    },
    {
      "id": 49,
      "name": "Kayleigh Cremin",
      "tel": "(122) 464-9775 x6528",
      "address": "62263 Schamberger Mountains",
      "opening_hours": "08:00",
      "description": "Molestiae qui dolorum omnis.",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=47.23822856124287",
      "viewCounts": 0,
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z",
      "CategoryId": 1,
      "Category": {
          "id": 1,
          "name": "中式料理",
          "createdAt": "2022-01-31T07:49:12.000Z",
          "updatedAt": "2022-01-31T07:49:12.000Z"
      },
      "isFavorited": false,
      "isLiked": false
    },
    {
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
      "isFavorited": false,
      "isLiked": false
    },
    {
      "id": 2,
      "name": "Josianne Morissette",
      "tel": "186-348-1096 x7161",
      "address": "98892 Nat Center",
      "opening_hours": "08:00",
      "description": "quisquam",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=7.247830906750674",
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
      "isFavorited": false,
      "isLiked": false
    }
  ],
  "categories": [
    {
      "id": 1,
      "name": "中式料理",
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z"
    },
    {
      "id": 2,
      "name": "日本料理",
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z"
    },
    {
      "id": 3,
      "name": "義大利料理",
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z"
    },
    {
      "id": 4,
      "name": "墨西哥料理",
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z"
    },
    {
      "id": 5,
      "name": "素食料理",
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z"
    },
    {
      "id": 6,
      "name": "美式料理",
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z"
    },
    {
      "id": 7,
      "name": "複合式料理",
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z"
    }
  ],
  "CategoryId": "",
  "page": 1,
  "totalPage": [
    1,
    2,
    3,
    4,
    5
  ],
  "prev": 1,
  "next": 2
}

export default {
  components: {
    NavTabs,
    RestaurantCard,
    RestaurantsNavPills,
    RestaurantsPagination
  },
  data () {
    return {
      restaurants: [],
      categories: [],
      CategoryId: -1,
      currentPage: 1,
      totalPage: [],
      previousPage: -1,
      nextPage: -1

    }
  },
  created() {
    this.fetchRestaurants()
  },
  methods: {
    fetchRestaurants () {
      const {
        restaurants,
        categories,
        CategoryId,
        page,
        totalPage,
        prev,
        next
      } = dummyData
      this.restaurants = restaurants
      this.categories = categories
      this.CategoryId = CategoryId
      this.currentPage = page
      this.totalPage = totalPage
      this.previousPage = prev
      this.nextPage = next
    }
  }
}
</script>