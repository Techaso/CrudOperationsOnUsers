<template>
    <div class="ui celled table grid">
        <tbody>
        <tr v-show="!Editing" class="center aligned">
            <td data-label="User Name" class="three wide column">{{user.username}}</td>
            <td data-label="Name" class="four wide column">{{user.name}}</td>
            <td data-label="Age" class="four wide column">{{user.age}}</td>
            <td data-label="Email" class="four wide column">{{user.email}}</td>
            <td data-label="Actions" class="four wide column">
                <span class='left floated edit icon' v-on:click="showForm">
                    <i class='edit icon'></i>
                </span>
                <span class='right floated trash icon' v-on:click="deleteUser(user)">
                    <i class='trash icon'></i>
                </span>
            </td>
        </tr>
        </tbody>

        <!-- form is visible when we are in editing mode -->
        <div v-show="Editing">
            <br>
        <div class='ui form'>

                <div class="ui table">
                    <tr class="center aligned">
                        <td>
                            <div class='field'>
                            <label>Name</label>
                            <input type='text' v-model="user.name" />
                            </div>
                        </td>
                        <td>
                            <div class='field'>
                            <label>Age</label>
                            <input type='text' v-model="user.age" />
                            </div>
                        </td>
                        <td>
                            <div class='field'>
                            <label>Email</label>
                            <input type='text' v-model="user.email" />
                            </div>
                        </td>
                        <td>
                            <div class="field">
                                <label>Action</label>
                            <button class='ui basic blue button' v-on:click="hideForm">
                                Save and Close
                            </button>
                            </div>
                            
                        </td>
                    </tr>
                </div>
                
        </div>
        <br>
        </div>
    </div>
</template>

<script>
export default {
    props:['user'],
    data() {
        return {
           Editing: false,
        };
    },
    methods:{
        deleteUser(user) {
            this.$emit('delete-user', user);
        },
        showForm(){
            this.Editing = true;
        },
        hideForm(){
            this.Editing = false;
        },
    }
}
</script>

<style>

</style>