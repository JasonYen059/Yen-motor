<template >
<div id="pipediv"> 
    <img v-if="showpipe == 21" class="pipeimg" src="../../public/pipe1.png">
    <img v-else class="pipeimg" src="../../public/pipe2.png">
</div>
</template>


<script>

export default {
    name:"pipe",
    data(){
        return{
        
        }
    },
    methods:{
        
    },

    props:
        ['showpipe'],

    
}
</script>

<style >
    #pipediv{
        position: absolute;
        right: 618px;
        top: 250px;
        z-index: 13;
    }
    .pipeimg{
        width: 430px;
        height: auto;
    }


</style>