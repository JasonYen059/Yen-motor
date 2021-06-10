<template>
    <transition-group tag="div" id="home" :name="transName">
        <div  v-for='img in imgs' :key="img.id" v-show="img.id === show">
            <img :src="img.src" width="100%" height="auto">
        </div>
        
    </transition-group>
</template>

<script>
export default {
    data(){
        return{
            transName:"fadein",
            show: 1,
            imgs:[
                {src:'work1.jpg',id:1},
                {src:'work2.jpg',id:2},
                {src:'work3.jpg',id:3},
                {src:'yen.jpg',id:4}
            ],
        }
    },
    mounted(){
        setInterval((()=>{
            if(this.show >= 4){
                this.show = 1;
            }else {
                this.show++;
            }
        }),5000)
    }
    
}
</script>

<style scoped>
#home {
    overflow: hidden;
    padding: 0;
    box-sizing: border-box;
    width: 100%;
    height: 100vh;
    position: absolute;
    top: 0;
}

img {
    position: absolute;
}

.fadein-enter-active,  .fadein-leave-active{
    transition: opacity 3s;
}
.fadein-enter, .fadein-leave-to {
    opacity: 0%;
}



</style>
