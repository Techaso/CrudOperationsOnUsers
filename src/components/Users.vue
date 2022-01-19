<template>
    <div class='ui'>
          <!-- Table for storing users data and actions buttons for them-->
          <table class="ui celled table">
            <thead>
              <tr class="center aligned">
                <th class="three wide column">User Name</th>
                <th class="four wide column">Name</th>
                <th class="four wide column">Age</th>
                <th class="four wide column">Email</th>
                <th class="three wide column">Actions</th>
              </tr>
            </thead>
      </table>
          <!-- load all users' data in the table  -->
          <user v-on:delete-user="deleteUser" v-for="user in users" v-bind:user="user" :key="user"></user>
          
    </div>
</template>

<script>
import User from './User.vue'
export default {
  // Bidirectionally binding this Users.vue script with App.vue, here like this and by v-bind:users='users' in App.vue
  props: ['users'],

  // This Users.vue script usages this components
  components:{
    User
  },
  methods: {
        // do this when a delete button is clicked
        deleteUser(user) {
            // find the index number of the delete button of the user (table row) which is clicked
            const userIndex = this.users.indexOf(user);
            // remove 1 element on userIndex index and overwrite the users array
            this.users.splice(userIndex, 1);
        }
    }
}
</script>


<style>
</style>
