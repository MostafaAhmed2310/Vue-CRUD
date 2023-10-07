<template>
    <button 
        :type="type" 
        :class="classBtn"
    >
        <i :class="icon"></i>
        {{btnText}}
    </button>
</template>

<script>
export default {
    name: 'PrimaryButton',
    props: {
        classBtn:String,
        btnText:String,
        type:String,
        icon: String
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
.m-7{
    margin: 0 7px;
}
</style>
