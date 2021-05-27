<template>
    <div >
    <inputcom @inputvalue="uphere($event)" :textToChild="backmsg"></inputcom>
    <hr>
    <h3>Yen.vue</h3>
    <p>出 生 : {{message}}</p>
    <button @click="backtochild()">Turn</button>
    </div>
</template>

<script>
import inputcom from '@/components/Inputcom.vue'

export default {
  components:{
    inputcom
  },
  methods:{
    uphere(e){
      this.message=e
    },
    backtochild(){
      this.backmsg = this.message+" "+"回去當蝌蚪"
    }
  },
  data(){
    return{
      message:"",
      backmsg:""
    }
  }
  
}
</script>

<style scoped>


</style>