<template>
    <!-- <div v-if="loader" class="loader-page">Loading...</div> -->
    <MainLoader v-if="loader"/>
    <LayoutTemp
        :users="users"
        :totalUsers="totalUsers"
        :limit="limit"
        @updateFetchUsersWithPagination="updateFetchUsersWithPagination"
        @deleteUser="deleteUser"
        @addNewUser="createNewUser"
    />
</template>

<script>
import LayoutTemp from '../Templates/Layout.Temp.vue';
import MainLoader from '@/components/Atoms/Loader/MainLoader.vue';
import { BaseUrl } from '@/config';

export default {
    name: 'LayoutPage',
    components: {
        LayoutTemp,
        MainLoader
    },
    props: {
        
    },
    data(){
        return{
            users: [],
            totalUsers: '',
            limit: '',
            loader: false,
            baseUrl: BaseUrl
        }
    },
    methods:{
        fetchallUsers(offset){
            this.loader = true;
            fetch(`${this.baseUrl}/users?offset=${offset}`)
            .then((response) => response.json())
            .then((json) => {
                this.users = json.users;
                this.totalUsers = json.total_users;
                this.limit = json.limit;
                this.loader = false
            });
            
        },
        updateFetchUsersWithPagination(offset){
            if(offset !== undefined){
                this.fetchallUsers(offset);
            }
        },

        //POST, PUT, DELETE NOt allowed methods in the APIs
        deleteUser(id){
            this.loader = true;
            fetch(`${this.baseUrl}/users/${id}`, {
                method: 'DELETE'
            })
            .then(response => {
                if (response.ok) {
                    this.fetchallUsers(0)
                } else {
                    console.error('Error deleting user:', response.statusText);
                }
                this.loader = false
            })
            .catch(error => {
                console.error('Error deleting user:', error);
            });
        },
        createNewUser(user){
            this.loader = true
            fetch(`${this.baseUrl}/users`, {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify(
                   user
                )
            })
           .then(response => {
                if (response.ok) {
                    this.loader = false
                } else {
                    this.loader = false
                    console.error('Error saving user:', response.statusText);
                }
            })
           .catch(error => {
                this.loader = false
                console.error('Error saving user:', error);
            });
        },
        editUser(){
            fetch(`https://api.slingacademy.com/v1/sample-data/users`, {
                method: 'Put',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify(
                   
                )
            })
           .then(response => {
                if (response.ok) {
                    console.log("res", response);
                } else {
                    console.error('Error saving user:', response.statusText);
                }
            })
           .catch(error => {
                console.error('Error saving user:', error);
            });
        },
    },
    mounted(){
        this.fetchallUsers(0);
    }
}
</script>

<style scoped>

</style>
