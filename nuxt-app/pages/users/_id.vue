<template>
  <h2>Пользователь {{ user.name }} </h2>
</template>

<script>
export default {
  validate ({ params }) {
    // Must be a number
    return /^\d+$/.test(params.id)
  },

  // computed: {
  //   id () {
  //     return this.$route.params.id
  //   }
  // }

  // Данная функция делает запрос на сервер, возвращает данные и создает "статичную страницу с контентом"
  async asyncData ({ params }) {
    const response = await fetch(`https://jsonplaceholder.typicode.com/users/${params.id}`)
    const user = await response.json()

    return {
      user
    }
  },

  data () {
    return {
      user: null, // Данное поле перезатирается данными из asyncData
      value: {} // Данное поле не будет перезатерено
    }
  }
}
</script>

<style>

</style>
