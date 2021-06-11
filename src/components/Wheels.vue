<template >
<div id="wheelsdiv"> 
    <img v-if="showwheels == 14" class="wheelsimg" src="../../public/wheels1818.png">
    <img v-else-if="showwheels == 15" class="wheelsimg" src="../../public/wheels1817.png">
    <img v-else class="wheelsimg" src="../../public/wheels1717.png">
</div>
</template>


<script>

export default {
    name:"wheels",
    data(){
        return{
           
        }
    },
    methods:{
        
    },

    props:
        ['showwheels'],

    
}
</script>

<style >
    #wheelsdiv{
        position: absolute;
        left: 306px;
        top: 265px;
        z-index: 1;
    }
    .wheelsimg{
        width: 940px;
        height: auto;
    }


</style>