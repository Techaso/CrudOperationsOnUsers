<template>
  <!-- Form for creating new user -->
    <div class='ui'>
    <p  v-show="!Creating">Click here to create a new user: <button class='ui basic button icon' v-on:click="openForm" v-show="!Creating">
      <i class='plus icon'></i>
    </button></p>
    <div class='ui centered card' v-show="Creating">
      <div class='content'>
        <div class='ui form'>
          <div class='field'>
            <label>User Name</label>
            <input type='text' v-model="usernameText" ref='username' defaultValue="" />
          </div>
          <div class='field'>
            <label>Name</label>
            <input type='text' v-model="nameText" ref='name' defaultValue="" />
          </div>
          <div class='field'>
            <label>Age</label>
            <input type='text' v-model="ageText" ref='age' defaultValue="" />
          </div>
          <div class='field'>
            <label>Email</label>
            <input type='text' v-model="emailText" ref='email' defaultValue="" />
          </div>
            <button class='ui basic green button' v-on:click="sendForm()">
              Create User
            </button>
            <button class='ui basic red button' v-on:click="closeForm">
              Close Form
            </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {

  // initial values for create user form fields, this is used for binding these variables with form inputs
  data() {
    return {
      usernameText: '',
      nameText: '',
      ageText: '',
      emailText: '',
      Creating: false,
    };
  },
  methods: {
    openForm() {
      this.Creating = true;
    },
    closeForm() {
      this.Creating = false;
    },
    sendForm() {
        // if all input data fields are not empty then emit 'create-user' named event with submitted data and catch this event in App.vue script using v-on:create-user="addUser". Define this addUser() function there
        if (this.usernameText.length > 0 && this.nameText.length > 0 && this.ageText.length > 0 && this.emailText.length > 0) {
            const username = this.usernameText;
            const name = this.nameText;
            const age = this.ageText;
            const email = this.emailText;
            this.$emit('create-user', {
            username,
            name,
            age,
            email,
            });
            this.newUserText = '';
        }
        // Close the form after data is submitted (create user button is clicked)
        this.Creating = false;
    }
  },
};
</script>