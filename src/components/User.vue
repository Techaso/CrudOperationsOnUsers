<template>
    <div>
        
        <tr v-show="!Editing" class="center aligned">
            <td data-label="User Name" class="center aligned">{{user.username}}</td>
            <td data-label="Name" class="center aligned">{{user.name}}</td>
            <td data-label="Age" class="center aligned">{{user.age}}</td>
            <td data-label="Email" class="center aligned">{{user.email}}</td>
            <td data-label="Actions" class="center aligned">
                <span class='left floated edit icon' v-on:click="showForm">
                    <i class='edit icon'></i>
                </span>
                <span class='right floated trash icon' v-on:click="deleteUser(user)">
                    <i class='trash icon'></i>
                </span>
            </td>
        </tr>

        <!-- form is visible when we are in editing mode -->
        <div v-show="Editing">
            <br>
        <div class='ui form'>
                <div class='field'>
                <label>Name</label>
                <input type='text' v-model="user.name" />
                </div>
                <div class='field'>
                <label>Age</label>
                <input type='text' v-model="user.age" />
                </div>
                <div class='field'>
                <label>Email</label>
                <input type='text' v-model="user.email" />
                </div>
                <div class='ui two button attached buttons'>
                <button class='ui basic blue button' v-on:click="hideForm">
                    Save and Close
                </button>
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