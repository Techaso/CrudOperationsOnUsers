<template>
  <div class="ui four column doubling stackable grid container">
    <div class='ui centered'>
      <table class="ui celled fixed table">
          <thead>
            <tr class="center aligned">
              <th>User Name</th>
              <th>Name</th>
              <th>Age</th>
              <th>Email</th>
              <th>Actions</th>
            </tr>
          </thead>
          <tbody>
            <user v-on:delete-user="deleteUser" v-for="user in users" v-bind:user="user" :key="user"></user>
          </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import User from './User.vue'
export default {
  props: ['users'],
  components:{
    User
  },
  methods: {
        deleteUser(user) {
            const userIndex = this.users.indexOf(user);
            this.users.splice(userIndex, 1);
        }
    }
}
</script>


<style>
</style>
