<template>
   <Layout
    :users="users"
    :totalUsers="totalUsers"
    :limit="limit"
    @updateFetchUsersWithPagination="this.$emit('updateFetchUsersWithPagination', pageStr)"
    @deleteUser="deleteUser"
    @addNewUser="addNewUser"
   />
</template>

<script>
import Layout from '@/components/Organisms/Layout/Layout.vue';

export default {
    name: 'LayoutTemp',
    components:{
        Layout
    },
    props: {
        users: Array,
        totalUsers: Number,
        limit: Number,
    },
    data(){
        return{}
    },
    methods:{
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

</style>
