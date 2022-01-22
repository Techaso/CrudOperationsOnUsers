<template><!-- Homepage -->
  <div id="app">
    <h1 style="color:green;">Users Management Page</h1>
    <p>Current total number of users: {{users.length}}</p>
    <!-- Create a new user -->
    <add-user-form v-on:create-user="addUser"></add-user-form><br><br>
    <!-- List of all users -->
    <Users v-bind:users="users"></Users>
  </div>
</template>

<script>
// for styling this web-app
import "semantic-ui-css/semantic.min.css";

// for including all the required components which are used in this App.vue script
import Users from './components/Users.vue';
import addUserForm from './components/addUserForm.vue';

export default {
  name: 'App',

  // Components/vue files which are used in this App.vue script
  components: {
    Users,
    addUserForm
  },
  // users data
  data() {
        return {
            users: [{
              username: 'rkkasotiya',
              name: 'Ramesh Kasotiya',
              age: 23,
              email: 'rkkasotiya@gmail.com',
            },
            {
              username: 'techaso',
              name: 'Techaso Kasotiya',
              age: 25,
              email: 'rktechaso@gmail.com',
            },
            {
              username: 'jitendra',
              name: 'Jitendra Kumar',
              age: 24,
              email: 'jitu@gmail.com',
            }]
        }
    },
    methods:{
      // do this when 'create-user' event happens in addUserForm.vue component
      addUser(data) {
        console.log('app.vue file ', data)
        this.users.push({
          username: data.username,
          name: data.name,
          age: data.age,
          email: data.email
      });
    }
    }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body {
  background-image: url("./assets/img/bg.png");
}
</style>
