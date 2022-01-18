<template>
    <div class='ui'>
          <table class="ui celled table">
            <thead>
              <tr class="center aligned">
                <th class="three wide column"> User Name</th>
                <th class="four wide column">Name</th>
                <th class="four wide column">Age</th>
                <th class="four wide column">Email</th>
                <th class="three wide column">Actions</th>
              </tr>
            </thead>
      </table>     
          <user v-on:delete-user="deleteUser" v-for="user in users" v-bind:user="user" :key="user"></user>
          
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
