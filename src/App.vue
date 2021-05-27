<template>
  <div id="app">
    <div id="routerContainer">
    <router-link to='/about'> about </router-link>
    <router-link to='/Yen' class="yen"> YenCustom </router-link>
    
    
    <router-view/>
    </div>
  </div>
</template>

<script>

export default {
  components:{},
  methods:{},
  data(){
    return{}
  }  
}
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

/* .router-link-active{
  color: orange;
} */
.yen {
  margin-left: 10px;
}
.router-link-exact-active{
  color:orange;
}

</style>
