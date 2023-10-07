<template>
    <h2>Customers List</h2>
    <hr>
    <div class="header-actions">
        <PrimaryButton
            btnText="View invoice"
            classBtn="btn btn-primary m-7"
            icon="fa-solid fa fa-eye"
            data-bs-toggle="modal" 
            data-bs-target="#viewInvoice"
        />
        <PrimaryButton
            btnText="Create New User"
            classBtn="btn btn-primary m-7"
            icon="fa-solid fa fa-plus"
            data-bs-toggle="modal" 
            data-bs-target="#addUserModal"

        />
    </div>
    <MainTable  
        :allUsers="users"
        @deleteUser="deleteUser"
    />
    <Pagination 
        @updatePagination="updatePagination"
        :totalUsers="totalUsers"
        :limit="limit"
    />
    <InvoiceModal/>
    <MainModal
        type="add"
        id="addUserModal"
        @addNewUser="addNewUser"
    />
</template>

<script>
import MainTable from '../../Molecules/Table/MainTable.vue';
import Pagination from "../../Atoms/Pagination/Pagination.vue";
import PrimaryButton from '@/components/Atoms/Button/PrimaryButton.vue';
import InvoiceModal from '@/components/Molecules/Modal/InvoiceModal.vue';
import MainModal from '@/components/Molecules/Modal/MainModal.vue';

export default {
    name: 'Lay-out',
    components:{
        MainTable,
        Pagination,
        PrimaryButton,
        InvoiceModal,
        MainModal
    },
    props: {
        users: Array,
        totalUsers: Number,
        limit: Number
    },
    data(){
        return{}
    },
    methods:{
        updatePagination(page){
            var pageStr = page.toString()+'0';
            pageStr = parseInt(pageStr);
            this.$emit('updateFetchUsersWithPagination', pageStr-10);
        },
        deleteUser(userId){
            this.$emit('deleteUser', userId);
        },
        addNewUser(user){
            this.$emit('addNewUser', user);
        }
    },
    mounted(){

    }
}
</script>

<style scoped>
.header-actions{
    margin-bottom: 20px;
    text-align: end;
}
</style>
