<template>
  <div id="app" :style="backimg">
      <div id="routerContainer">
        <router-link to='/home' class="pages"> H O M E </router-link>
        <router-link to='/about' class="pages"> A B O U T </router-link>
        <router-link to='/Yen' class="pages"> C U S T O M </router-link> 
      <transition name="slide" >
        <router-view/>
      </transition>
      </div>  
  </div>
</template>

<script>

export default {
  methods:{},
  data(){
    return{
      backimg:{
        // backgroundImage:'url(/work1.jpg)',
        width:'100%',
        minHeight:'100vh',
        backgroundSize:'cover'
      }
    }
  }  
}
</script>


<style >

#app {
  color: #2c3e50;
  background-color: #5c5c5c;
}

.pages {
  margin: 15px;
  color: rgb(138, 138, 138);
  font-size: 20px;
  text-decoration-line: none;
  position: relative;
  left: 600px;
  top: 20px;
  z-index: 6;
}

.pages:hover {
  color: #f5f5f5;
  transition: all 1s ease;
}

#routerContainer {
  width: 100%;
  min-height: 100vh;
  
}

.router-link-exact-active{
  color: rgb(187, 185, 185);
  padding: 10px 0;
  border-bottom: 2px solid rgb(187,185,185);
}
.slide-enter-active,
.slide-leave-active{
  transition: opacity 1s 
}
.slide-enter,
.slide-leave-to {
  opacity: 0;
  
}

</style>
