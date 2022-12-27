<template>
  <div class="user-card">
    <div class="max-w-sm m-1 bg-white border border-gray-200 rounded-lg shadow-md dark:bg-gray-800 dark:border-gray-700 text-center">
      <a href="#">
        <img class="rounded-t-lg mx-auto" :src="`https://robohash.org/${user.id}?size=300x300`" alt=""/>
      </a>
      <div class="p-5">
        <a href="#">
          <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">{{ user.name }}</h5>
        </a>
        <p class="mb-3 font-normal text-gray-700 dark:text-gray-400">
          {{ user.email }}
        </p>
        <p class="mb-3 font-normal text-gray-700 dark:text-gray-400 only-on-hover">
          {{user.bio}}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "UserCard",
  props: {
    user: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.user-card {
  width: 300px;
}
.only-on-hover {
  display: none;
}
.user-card:hover .only-on-hover {
  display: block;
}
</style>