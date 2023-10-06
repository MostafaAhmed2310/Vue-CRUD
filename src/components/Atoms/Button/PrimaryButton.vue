<template>
    <button 
        :type="type" 
        :class="calssBtn"
    >
        {{btnText}}
    </button>
</template>

<script>
export default {
    name: 'PrimaryButton',
    props: {
        calssBtn:String,
        btnText:String,
        type:String
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
