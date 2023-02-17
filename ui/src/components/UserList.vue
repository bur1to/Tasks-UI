<template>
    <div>
        <h3 class="h3">Table</h3>
        <table class="table">
            <thead>
                <th>Username</th>
                <th>Email</th>
                <th>Age</th>
            </thead>
            <tbody>
                <tr v-for="user in users" :key="user._id">
                    <td>
                        <RouterLink :to="'/user/' + user._id" class="route_style">
                            <a>
                              {{ `${user.firstName} ${user.lastName}` }}
                            </a>
                        </RouterLink>
                    </td>
                    <td>{{ user.email }}</td>
                    <td>{{ user.age }}</td>
                </tr>
            </tbody>
        </table>
    </div>
    <div class="page__wrapper">
        <div class="page" v-for="pageNumber in totalPages" :key="pageNumber" :class="{
            'current-page': page === pageNumber
        }" @click="changePage(pageNumber)">
            {{ pageNumber }}
        </div>
</div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      users: [],
      page: 1,
      limit: 5,
      sort: 'firstName',
      sortBy: 'asc',
      totalPages: 0,
      selectedOptions: [
        { value: 'firstName', name: 'first name' },
        { value: 'lastName', name: 'last name' },
        { value: 'email', name: 'email' },
      ]
    }
  },    
  methods: {
    async changePage(pageNumber) {
      this.page = pageNumber;
      this.getUsers({ page: pageNumber - 1 });
    },
    async getUsers(params) {
      const { data } = await axios.get('http://localhost:3000/users', { params });
      this.users = data.users;
      this.totalPages = Math.ceil(data.count / this.limit);
    }
  },
  mounted() {
    this.getUsers();
  }
}
</script>

<style>
.h3 {
    text-align: center;
}

.table {
    border-collapse: collapse;
    border: 2px solid #6A5ACD;
    margin: auto;
}

thead {
    text-align: left;
}

th,
td {
    border: 2px solid #6A5ACD;
    padding: 10px;
    min-width: 200px;
}

a {
    text-decoration: none;
}

a:visited {
    color: purple;
}

.route_style {
    color: #6A5ACD;
}

.page__wrapper {
    display: flex;
    margin-top: 15px;
    justify-content: center;
}

.page {
    border: 1px solid black;
    padding: 8px;
    margin-right: 10px;
}

.current-page {
    border: 2.5px solid #6A5ACD;
}</style>
