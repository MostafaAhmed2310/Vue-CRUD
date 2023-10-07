<template>
    <v-pagination
        v-model="page"
        :pages="totalUsers/limit"
        :range-size="limit"
        active-color="#DCEDFF"
        @update:modelValue="updateHandler"
    />
</template>

<script>
import VPagination from "@hennge/vue3-pagination";
import "@hennge/vue3-pagination/dist/vue3-pagination.css";

export default {
    name: 'Table-Pagination',
    props: {
        totalUsers: Number,
        limit: Number
    },
    components:{
        VPagination
    },
    data(){
        return{
            page: 1
        }
    },
    methods:{
        updateHandler(e){
            this.page = e
            this.$emit('updatePagination', this.page);
        }
    },
    mounted(){

    }
}
</script>

<style scoped>

</style>
