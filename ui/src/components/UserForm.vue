<template>
    <form @submit.prevent>
        <h4>Create user</h4>
        <h5>Fields with * is required</h5>
        <input v-model="user.firstName" class="input" placeholder="First name*">
        <input v-model="user.lastName" class="input" placeholder="Last name*">
        <input v-model="user.email" class="input" placeholder="example@example.com*">
        <input v-model="user.password" class="input" placeholder="password*">
        <input v-model="user.age" class="input" placeholder="age*">
        <my-button @click="createUser">Create</my-button>
</form>
</template>

<script>
import axios from 'axios';

export default {
    data() {
        return {
            user: {
                firstName: '',
                lastName: '',
                email: '',
                password: '',
                age: ''
            }
        }
    },
    methods: {
        async createUser() {
            await axios.post('http://localhost:3000/users', this.user)
                .then((res) => console.log(res))
                .catch((err) => console.log(err));

            this.$emit('create', thus.user);
            this.user = {
                firstName: '',
                lastName: '',
                email: '',
                password: '',
                age: ''
            };
        }
    }
}
</script>

<style>
form {
    display: flex;
    flex-direction: column;
}

.input {
    width: 300px;
    border: 1px solid #6A5ACD;
    padding: 10px 15px;
    margin-top: 15px;
}
</style>
