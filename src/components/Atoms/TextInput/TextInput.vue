<template>
    <input v-model="value" :type="type" :name="name" :id="id" :value2="value2">
</template>

<script>
export default {
    name: 'TextInput',
    props: {
        type: String,
        name: String,
        id: String,
    },
    data(){
        return{
            
        }
    },
    methods:{
        
    },
    mounted(){

    }
}
</script>

<style scoped>

</style>
