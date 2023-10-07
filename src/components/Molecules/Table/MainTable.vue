<template>
    <div>
        <table class="table">
            <thead>
                <tr>
                    <th>Avatar</th>
                    <th>Name</th>
                    <th>Email</th>
                    <th>Phone number</th>
                    <th>Description</th>
                    <th>Actions</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="user in allUsers" :key="user">
                    <td><img class="profile-pic" :src="user.profile_picture" alt=""></td>
                    <td>{{ `${user.first_name} ${user.last_name}` }}</td>
                    <td>{{ user.email }}</td>
                    <td>{{ user.phone }}</td>
                    <td><div class="rich-text">{{ user.description }}</div></td>
                    <td>
                        <PrimaryButton data-bs-toggle="modal" data-bs-target="#viewUserModal" @click="viewUser(user)" classBtn="btn btn-primary m-7" icon="fa-solid fa fa-eye"/>
                        <PrimaryButton data-bs-toggle="modal" data-bs-target="#editUserModal" @click="viewUser(user)" classBtn="btn btn-success m-7" icon="fa-solid fa fa-pencil"/>
                        <PrimaryButton data-bs-toggle="modal" data-bs-target="#deleteUserModal" @click="viewUser(user)" classBtn="btn btn-danger m-7" icon="fa-solid fa fa-trash"/>
                    </td>
                </tr>
            </tbody>
        </table>

        <MainModal
            id="viewUserModal"
            type="view"
            :user="currentUser"
        />
        <MainModal
            id="editUserModal"
            type="edit"
            :user="currentUser"
        />
        <MainModal
            id="deleteUserModal"
            type="delete"
            :user="currentUser"
            @deleteUser="deleteUser"
        />
    </div>
    
</template>

<script>
import PrimaryButton from '@/components/Atoms/Button/PrimaryButton.vue';
import MainModal from '@/components/Molecules/Modal/MainModal.vue';

export default {
    name: 'Main-table',
    props: {
        allUsers: Array
    },
    components:{
        PrimaryButton,
        MainModal
    },
    data(){
        return{
            currentUser: {}
        }
    },
    methods:{
        viewUser(user){
            this.currentUser = user;
        },
        editUser(user){
            this.editingUser = user;
        },
        deleteUser(userId){
            this.$emit('deleteUser', userId)
        },
    },
    mounted(){

    }
}
</script>

<style scoped>
    .profile-pic{
        width: 20px;
        height: 20px;
        border-radius: 50%;
        box-shadow: 1px 1px 4px 1px #ddd;
    }
</style>