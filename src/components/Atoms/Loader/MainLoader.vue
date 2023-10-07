<template>
    <div class="loader-container">
        <div class="spinner-border text-primary" role="status">
            <span class="visually-hidden">Loading...</span>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Main-Loader',
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
.loader-container{
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    text-align: center;
    line-height: 100vh;
    background: #fff;
    z-index: 9999
}
</style>
