<template>
    <Navbar/>
    <MainTable/>
    <Pagination/>
</template>

<script>
import Navbar from '../../Molecules/Navbar/Navbar.vue';
import MainTable from '../../Molecules/Table/Table.vue';
import Pagination from "../../Atoms/Pagination/Pagination.vue";

export default {
    name: 'Lay-out',
    components:{
        Navbar,
        MainTable,
        Pagination
    },
    props: {
        
    },
    data(){
        return{}
    },
    methods:{
        
    },
    mounted(){

    }
}
</script>

<style scoped>

</style>
