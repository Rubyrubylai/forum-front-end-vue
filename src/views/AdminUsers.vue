<template>
  <div class="container py-5">
    <!-- AdminNav Component -->
    <AdminNav />

    <table class="table">
      <thead class="thead-dark">
        <tr>
          <th scope="col">#</th>
          <th scope="col">Email</th>
          <th scope="col">Role</th>
          <th scope="col" width="140">Action</th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="user in users"
          :key="user.id"
        >
          <th scope="row">{{user.id}}</th>
          <td>{{user.email}}</td>
          <td>{{user.isAdmin ? 'admin': 'user'}}</td>
          <td>
            <button
              v-if="user.id != currentUser.id"
              type="button"
              class="btn btn-link"
              @click.stop.prevent="toggleUserRole(user.id)"
            >set as {{user.isAdmin ? 'admin': 'user'}}</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import AdminNav from "@/components/AdminNav";

const dummyUser = {
  currentUser: {
    id: 1,
    name: '管理者',
    email: 'root@example.com',
    image: 'https://i.pravatar.cc/300',
    isAdmin: true
  },
  isAuthenticated: true
}

const dummyData = {
  users: [
    {
      id: 1,
      name: "root",
      email: "root@example.com",
      password: "$2a$10$lhQQRzd.MiI7bFp/Hnwx8upe8.6gEX7a6bsRKwgLC88on0M3UiR9a",
      isAdmin: true,
      image: null,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
    },
    {
      id: 2,
      name: "user1",
      email: "user1@example.com",
      password: "$2a$10$hiu0H/XQNx/AFiPmiBJA7uc7IBHMYmbrNWQGlvr.nNFmA8IU.ljdW",
      isAdmin: false,
      image: null,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
    },
    {
      id: 3,
      name: "user2",
      email: "user2@example.com",
      password: "$2a$10$oeZAkhtCQTk/KQ2N4pkp..S93mPXWZ3bngAOyJDo70V.TSs3YMXCS",
      isAdmin: false,
      image: null,
      createdAt: "2022-01-31T07:49:12.000Z",
      updatedAt: "2022-01-31T07:49:12.000Z",
    },
  ],
};

export default {
  components: {
    AdminNav,
  },
  data() {
    return {
      users: '',
      currentUser: dummyUser.currentUser
    }
  },
  created() {
    this.fetchUser()
  },
  methods: {
    fetchUser() {
      this.users = dummyData.users
    },
    toggleUserRole(UserId) {
      this.users = this.users.map(user => {
        if (user.id === UserId) {
          return {
            ...user,
            isAdmin: !user.isAdmin
          }
        }

        return user
      })
    }
  }
};
</script>
