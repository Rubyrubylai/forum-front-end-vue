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

const dummyData = {
  "restaurants": [
    {
      "id": 50,
      "name": "Alexie Pacocha",
      "tel": "(249) 322-0854",
      "address": "199 Erdman Trafficway",
      "opening_hours": "08:00",
      "description": "Dolorem ut corrupti. Dolores ut occaecati sunt qua",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=12.248914951124569",
      "viewCounts": 0,
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z",
      "CategoryId": 4,
      "FavoritedUsers": [],
      "isFavorited": false,
      "FavoriteCount": 0
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
      "FavoritedUsers": [],
      "isFavorited": false,
      "FavoriteCount": 0
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
      "FavoritedUsers": [],
      "isFavorited": false,
      "FavoriteCount": 0
    },
    {
      "id": 47,
      "name": "Harold Jacobson",
      "tel": "(858) 695-6808",
      "address": "63463 Buck Stream",
      "opening_hours": "08:00",
      "description": "et",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=67.26227176332283",
      "viewCounts": 0,
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z",
      "CategoryId": 3,
      "FavoritedUsers": [],
      "isFavorited": false,
      "FavoriteCount": 0
    },
    {
      "id": 46,
      "name": "Everardo Reichel",
      "tel": "712-859-2804",
      "address": "0114 Corrine Views",
      "opening_hours": "08:00",
      "description": "At et enim.\nEa dignissimos quibusdam voluptatem ne",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=71.15578389427839",
      "viewCounts": 0,
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z",
      "CategoryId": 2,
      "FavoritedUsers": [],
      "isFavorited": false,
      "FavoriteCount": 0
    },
    {
      "id": 45,
      "name": "Alia O'Conner Sr.",
      "tel": "872-301-8435 x7758",
      "address": "68771 Hammes Row",
      "opening_hours": "08:00",
      "description": "Quasi eius sequi sunt sapiente vel.\nImpedit quaera",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=1.0481977419990685",
      "viewCounts": 0,
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z",
      "CategoryId": 3,
      "FavoritedUsers": [],
      "isFavorited": false,
      "FavoriteCount": 0
    },
    {
      "id": 44,
      "name": "Ed Stracke",
      "tel": "1-658-666-5909",
      "address": "50571 Runte Greens",
      "opening_hours": "08:00",
      "description": "incidunt dignissimos porro",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=91.0493955495603",
      "viewCounts": 0,
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z",
      "CategoryId": 5,
      "FavoritedUsers": [],
      "isFavorited": false,
      "FavoriteCount": 0
    },
    {
      "id": 43,
      "name": "Leilani Farrell",
      "tel": "1-762-367-5029 x505",
      "address": "9624 Gleason Forest",
      "opening_hours": "08:00",
      "description": "Autem cupiditate blanditiis facere ullam hic conse",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=98.88613237043953",
      "viewCounts": 0,
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z",
      "CategoryId": 5,
      "FavoritedUsers": [],
      "isFavorited": false,
      "FavoriteCount": 0
    },
    {
      "id": 42,
      "name": "Ellis Borer",
      "tel": "(483) 157-8015",
      "address": "543 Adolfo Route",
      "opening_hours": "08:00",
      "description": "Rerum magnam non dolorem. Odit quia eveniet nulla ",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=43.963422673486896",
      "viewCounts": 0,
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z",
      "CategoryId": 3,
      "FavoritedUsers": [],
      "isFavorited": false,
      "FavoriteCount": 0
    },
    {
      "id": 41,
      "name": "Rodger Cassin",
      "tel": "725.174.1801 x48546",
      "address": "321 Marlin Highway",
      "opening_hours": "08:00",
      "description": "Voluptas exercitationem quo eius non.\nMagnam harum",
      "image": "https://loremflickr.com/320/240/restaurant,food/?random=67.45064701988537",
      "viewCounts": 0,
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z",
      "CategoryId": 5,
      "FavoritedUsers": [],
      "isFavorited": false,
      "FavoriteCount": 0
    }
  ]
}

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
    fetchRestaurants() {
      this.restaurants = dummyData.restaurants
    }
  }
}
</script>