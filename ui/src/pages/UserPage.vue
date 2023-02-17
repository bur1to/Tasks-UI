<template>
    <div class="user">
        <h3>{{ `${user.firstName} ${user.lastName}` }}</h3>
        <div><strong>Email: </strong>{{ user.email }}</div>
        <div><strong>Age: </strong>{{ user.age }}</div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    data() {
        return {
            user: [],
        }
    },
    methods: {
        async getUser() {
            const { data } = await axios.get(`http://localhost:3000/users/${this.$route.params.id}`);
            this.user = data;
        }
    },
    mounted() {
        this.getUser();
    }
}
</script>

<style>
.user {
    padding: 15px;
    border: 2px solid #6A5ACD;
    margin-top: 15px;
}
</style>
