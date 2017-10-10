<template>
    <div>
        <table class="table table-striped">
            <thead>
                <tr>
                    <th>使用者名稱</th>
                    <th>email</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="user in users">
                    <td>{{ user.username }}</td>
                    <td>{{ user.email }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
    export default {
        ready() {
            console.log('Component ready.')
        },
        data() {
            return {
                users: []
            }
        },
        created() {
            this.fetchUsers();
        },
        methods: {
            fetchUsers() {
                this.$http.get('/users').then(response =>{
                    this.users = response.data.users;
                })
            }
        }
    }
</script>
