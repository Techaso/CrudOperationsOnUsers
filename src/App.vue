<template>
  <div id="app">
    <p>Current total number of users: {{users.length}}</p>
    <add-user-form v-on:create-user="addUser"></add-user-form>
    <br>
    <br>
    <Users v-bind:users="users"></Users>
  </div>
</template>

<script>
import "semantic-ui-css/semantic.min.css";
import Users from './components/Users.vue'
// import CreateUser from './components/CreateUser.vue';
import addUserForm from './components/addUserForm.vue';

export default {
  name: 'App',
  components: {
    Users,
    // CreateUser,
    addUserForm
  },
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
</style>
