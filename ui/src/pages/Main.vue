<template>
    <div>
        <h4>Users</h4>
        <my-button @click="showDialog">Create user</my-button>
        <my-dialog v-model:show="dialogVisible">
            <user-form @create="createUser"/>
        </my-dialog>
        <user-list :users="users"/>
    </div>
</template>

<script>
import UserForm from '@/components/UserForm.vue';
import UserList from '@/components/UserList.vue';

export default {
    components: {
        UserForm,
        UserList
    },
    data() {
        return {
            users: [],
            dialogVisible: false
        }
    },
    methods: {
        showDialog() {
            this.dialogVisible = true;
        },
        createUser(user) {
            this.users.push(user);
            this.dialogVisible = false;
        }
    }
}
</script>

<style>
</style>
