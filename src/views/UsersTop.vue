<template>
  <div class="container py-5">
    <NavTabs />
    <h1 class="mt-5">
      美食達人
    </h1>
    <hr>
    <div class="row text-center">
      <UserCard
        v-for="user in users"
        :key="user.id"
        :initial-user="user"
      />
    </div>
  </div>
</template>

<script>
import NavTabs from '../components/NavTabs.vue'
import UserCard from '../components/UserCard.vue'

const dummyData = {
  "users": [
    {
      "id": 1,
      "name": "root",
      "email": "root@example.com",
      "password": "$2a$10$lhQQRzd.MiI7bFp/Hnwx8upe8.6gEX7a6bsRKwgLC88on0M3UiR9a",
      "isAdmin": true,
      "image": null,
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z",
      "Followers": [],
      "FollowerCount": 0,
      "isFollowed": false
    },
    {
      "id": 2,
      "name": "user1",
      "email": "user1@example.com",
      "password": "$2a$10$hiu0H/XQNx/AFiPmiBJA7uc7IBHMYmbrNWQGlvr.nNFmA8IU.ljdW",
      "isAdmin": false,
      "image": null,
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z",
      "Followers": [],
      "FollowerCount": 0,
      "isFollowed": false
    },
    {
      "id": 3,
      "name": "user2",
      "email": "user2@example.com",
      "password": "$2a$10$oeZAkhtCQTk/KQ2N4pkp..S93mPXWZ3bngAOyJDo70V.TSs3YMXCS",
      "isAdmin": false,
      "image": null,
      "createdAt": "2022-01-31T07:49:12.000Z",
      "updatedAt": "2022-01-31T07:49:12.000Z",
      "Followers": [],
      "FollowerCount": 0,
      "isFollowed": false
    }
  ]
}

export default {
  components: {
    NavTabs,
    UserCard
  },
  data() {
    return {
      users: []
    }
  },
  created() {
    this.fetchUser()
  },
  methods: {
    fetchUser() {
      this.users = dummyData.users
    }
  }
}
</script>