<template>
  <div class="m-4">
    <div class="my-2">
      <label for="search" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Search here</label>
      <input v-model="search" type="text" id="search" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="Type here" required>
    </div>
    <div class="flex items-center justify-center flex-wrap">
      <user-card :user="user" v-for="user in searchedUser" :key="user.id" class="d-flex"/>
    </div>
  </div>
</template>

<script>
import UserCard from "@/components/UserCard.vue";
import axios from "axios";

export default {
  name: "HomeView",
  components: {UserCard},
  data() {
    return {
      users: [],
      search: ''
    }
  },
  computed:{
    searchedUser(){
      if (this.search === '') {
        return this.users
      } else {
        return this.users.filter(user => user.name.toLowerCase().includes(this.search.toLowerCase()))
      }
    }
  },
  mounted() {
    this.getUsers()
  },
  methods: {
    getUsers() {
      const url = "http://52.77.211.222:3000/users"
      axios.get(url).then(response => {
        this.users = response.data
      })
    }
  }
}
</script>

<style scoped>

</style>