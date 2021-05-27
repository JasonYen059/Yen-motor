<template>
<div>
    <h3>Inputcom</h3>
    <input type="text" v-model="typein" @keyup.enter="upup()">
    <p>Back : {{textToChild}}</p>
</div>
    
</template>

<script>
export default {
    name:"inputcom",
    data(){
        return{
           typein:'' 
        }
    },
    props:{textToChild:String},
    
    methods:{
        upup(){
            this.$emit('inputvalue',this.typein);
            this.typein='';
        }
    }
    
}
</script>

<style scoped>

</style>