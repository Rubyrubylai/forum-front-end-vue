<template>
  <div class="container py-5">
    <RestaurantDetail
      :initial-restaurant="restaurant"
      :current-user="currentUser"
    />
    <hr>
    <RestaurantComments
      :restaurant-comments="restaurantComments"
      @after-delete-comment="afterDeleteComment"
    />
    
    <CreateComment
      :restaurant-id="restaurant.id"
      @create-comment="afterCreateComment"
    />
  </div>
</template>

<script>
import { mapState } from 'vuex'
import RestaurantDetail from '../components/RestaurantDetail.vue'
import RestaurantComments from '../components/RestaurantComments.vue'
import CreateComment from '../components/CreateComment.vue'
import restaurantsAPI from '../apis/restaurants'
import { Toast } from '../utils/helpers'

export default {
  components: {
    RestaurantDetail,
    RestaurantComments,
    CreateComment
  },
  data () {
    return {
      restaurant: {
        id: -1,
        name: '',
        categoryName: '',
        image: '',
        openingHours: '',
        tel: '',
        address: '',
        description: '',
        isFavorited: false,
        isLiked: false
      },
      restaurantComments: [],
    }
  },
  created () {
    const { id: restaurantId } = this.$route.params
    this.fetchRestaurant(restaurantId)
  },
  computed: {
    ...mapState(['currentUser'])
  },
  beforeRouteUpdate(to, from, next) {
    const { id: restaurantId } = to.params
    this.fetchRestaurant(restaurantId)
    next()
  },
  methods: {
    async fetchRestaurant (restaurantId) {
      try {
        const { data } = await restaurantsAPI.getRestaurant({ restaurantId })

        this.restaurant = {
          id: data.restaurant.id,
          name: data.restaurant.name,
          categoryName: data.restaurant.Category.name,
          image: data.restaurant.image,
          openingHours: data.restaurant.opening_hours,
          tel: data.restaurant.tel,
          address: data.restaurant.address,
          description: data.restaurant.description,
          isFavorited: data.isFavorited,
          isLiked: data.isLiked,
        }

        this.restaurantComments = data.restaurant.Comments
      } catch (error) {
        Toast.fire({
          icon: 'error',
          title: '無法取得餐廳資料，請稍後再試'
        })
      }
    },
    async afterDeleteComment(commentId) {
      try {
        const { data } = await restaurantsAPI.deleteComment({ commentId })

        if (data.status !== 'success') {
          return new Error(data.message)
        }

        this.restaurantComments = this.restaurantComments.filter(comment => comment.id !== commentId)
      } catch (error) {
        Toast.fire({
          icon: 'error',
          title: '無法刪除評論，請稍後再試'
        })
      }
    },
    async afterCreateComment(payload) {
      try {
        const { restaurantId, text } = payload

        const { data } = await restaurantsAPI.createComment({ restaurantId, text })

        if (data.status !== 'success') {
          return new Error (data.message)
        }

        this.restaurantComments.push({
          id: data.commentId,
          RestaurantId: restaurantId,
          User: {
            id: this.currentUser.id,
            name: this.currentUser.name
          },
          text,
          createdAt: new Date()
        })
      } catch (error) {
        Toast.fire({
          icon: 'error',
          title: '無法新增評論，請稍後再試'
        })
      }
    }
  }
}
</script>
