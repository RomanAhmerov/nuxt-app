<template>
  <div>
    <h1 class="header">
      Пользователи
    </h1>
    <ul>
      <li
        v-for="user in users"
        :key="user.id"
      >
        <nuxt-link :to="`users/${user.id}`">{{ user.name }}</nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
// import { mapGetters } from 'vuex'

export default {
  // layout: 'test',
  // computed: {
  //   ...mapGetters({
  //     users: 'users/getUsers'
  //   })
  // }

  // Данная функция делает контент "статичным"
  async asyncData () {
    const response = await fetch('https://jsonplaceholder.typicode.com/users')
    const users = await response.json()

    return {
      users
    }
  },

  data () {
    return {
      users: [], // Перезатреться значениями из asyncData
      values: [] // Не перезатреться
    }
  }
}
</script>

<style scoped>
.header {
  color: red;
}
</style>
