<template>
    <div>
        <table class="table">
            <thead>
                <tr>
                    <th>Name</th>
                    <th>Email</th>
                    <th>Description</th>
                    <th>Actions</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="user in users" :key="user.id">
                    <td>{{ user.name }}</td>
                    <td>{{ user.email }}</td>
                    <td><div class="rich-text">{{ user.description }}</div></td>
                    <td>
                        <button data-bs-toggle="modal" data-bs-target="#viewUserModal" @click="viewUser(user)">View</button>
                        <button @click="editUser(user)">Edit</button>
                        <button @click="deleteUser(user.id)">Delete</button>
                    </td>
                </tr>
            </tbody>
        </table>

        <div class="modal fade" id="viewUserModal" tabindex="-1" aria-labelledby="viewUserModalLabel" aria-hidden="true">
            <div class="modal-dialog">
                <div class="modal-content">
                    <div class="modal-header">
                        <h5 class="modal-title" id="viewUserModalLabel">View User</h5>
                        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                    </div>
                    <div class="modal-body">
                        <form>
                            <div class="mb-3">
                                <label for="name" class="form-label">Name</label>
                                <input type="text" class="form-control" id="name" v-model="viewingUser.name" disabled>
                            </div>
                            <div class="mb-3">
                                <label for="email" class="form-label">Email</label>
                                <input type="email" class="form-control" id="email" v-model="viewingUser.email" disabled>
                            </div>
                            <div class="mb-3">
                                <label for="description" class="form-label">Description</label>
                                <textarea class="form-control" id="description" rows="3" v-model="viewingUser.description" disabled></textarea>
                            </div>
                        </form>
                    </div>
                    <div class="modal-footer">
                        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
                    </div>
                </div>
            </div>
        </div>

        <div class="modal fade" id="editUserModal" tabindex="-1" aria-labelledby="editUserModalLabel" aria-hidden="true">
            <div class="modal-dialog">
                <div class="modal-content">
                    <div class="modal-header">
                        <h5 class="modal-title" id="editUserModalLabel">Edit User</h5>
                        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                    </div>
                    <div class="modal-body">
                        <form>
                            <div class="mb-3">
                                <label for="name" class="form-label">Name</label>
                                <input type="text" class="form-control" id="name" v-model="editingUser.name">
                            </div>
                            <div class="mb-3">
                                <label for="email" class="form-label">Email</label>
                                <input type="email" class="form-control" id="email" v-model="editingUser.email">
                            </div>
                            <div class="mb-3">
                                <label for="description" class="form-label">Description</label>
                                <textarea class="form-control" id="description" rows="3" v-model="editingUser.description"></textarea>
                            </div>
                        </form>
                    </div>
                    <div class="modal-footer">
                        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
                        <button type="button" class="btn btn-primary" @click="saveUser">Save changes</button>
                    </div>
                </div>
            </div>
        </div> 
    </div>
</template>

<script>
export default {
    name: 'Main-table',
    props: {

    },
    data(){
        return{
            users: [
                { id: 1, name: 'John Doe', email: 'john.doe@example.com', description: 'This is some rich text formatted description.' },
                { id: 2, name: 'Jane Smith', email: 'jane.smith@example.com', description: 'This is another rich text formatted description.' }
            ],
            viewingUser: { id: 1, name: 'John Doe', email: 'john.doe@example.com', description: 'This is some rich text formatted description.' },

            editingUser: { id: 1, name: 'John Doe', email: 'john.doe@example.com', description: 'This is some rich text formatted description.' },
        }
    },
    methods:{
        viewUser(user){
            console.log(user);
            this.viewingUser = user;
        },
        editUser(user){
            this.editingUser = user;
        },
        saveUser(){
            fetch(`https://example.com/api/users/${this.editingUser.id}`, {
                method: 'PUT',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify(this.editingUser)
            })
           .then(response => {
                if (response.ok) {
                    this.editingUser = null;
                    this.users = this.users.map(user => {
                        if (user.id === this.editingUser.id) {
                            return this.editingUser;
                        } else {
                            return user;
                        }
                    });
                } else {
                    console.error('Error saving user:', response.statusText);
                }
            })
           .catch(error => {
                console.error('Error saving user:', error);
            });
        },
        deleteUser(id){
            fetch(`https://example.com/api/users/${id}`, {
                method: 'DELETE'
            })
          .then(response => {
                if (response.ok) {
                    this.users = this.users.filter(user => user.id!== id);
                } else {
                    console.error('Error deleting user:', response.statusText);
                }
            })
          .catch(error => {
                console.error('Error deleting user:', error);
            });
        }
    },
    mounted(){

    }
}
</script>