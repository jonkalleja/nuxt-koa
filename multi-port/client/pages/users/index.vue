<template>
  <section class="container">
    <h1 class="title">
      USERS
    </h1>
    <ul class="users">
      <!-- <li v-for="(user, index) in $store.state.users" :key="index" class="user"> -->
      <li v-for="(user, index) in users" :key="index" class="user">
        <nuxt-link :to="'users/' + index">
          {{ user.name }}
        </nuxt-link>
      </li>
    </ul>
  </section>
</template>

<script>
import axios from '~/plugins/axios'
// import store from '~/store'

export default {
  async asyncData () {
    let { data } = await axios.get('/users')
    var users = data.data
    console.log(users)
    return { users: users }
  },
  // // Or using store.
  // async fetch ({ store, params }) {
  //   let { data } = await axios.get('/users')
  //   store.commit('setUsers', data.data)
  // },
  head () {
    return {
      title: 'Users'
    }
  }
}
</script>

<style scoped>
.title
{
  margin: 30px 0;
}
.users
{
  list-style: none;
  margin: 0;
  padding: 0;
}
.user
{
  margin: 10px 0;
}
</style>
