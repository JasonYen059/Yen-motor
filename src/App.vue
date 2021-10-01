<template>
  <div id="app" >
      <div class="routerContainer">
        <router-link to='/' class="pages"> H O M E </router-link>
        <router-link to='/about' class="pages"> A B O U T </router-link>
        <router-link to='/Yen' class="pages"> C U S T O M </router-link> 
      </div> 
      <transition name="slide" >
        <router-view/>
      </transition>
      
  </div>
</template>

<script>

export default {
  methods:{
    hide(){
      this.testshow = false
    }
  },
  data(){
    return{
      testshow:true,
      }
    }
  }  
</script>


<style >

.routerContainer {
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 2;
  padding-top: 15px;
  width: 100%;
  height: 10%;
}

.pages {
  margin:0 2vw;
  color: rgb(138, 138, 138);
  font-size: 2vw;
  text-decoration-line: none;
  z-index: 2;
  padding-bottom: 10px;
  text-align: center;
}

.pages:hover {
  color: #f5f5f5;
  transition: all 1s ease;
}

.router-link-exact-active{
  color: rgb(187, 185, 185);
  border-bottom: 2px solid rgb(187,185,185);

}
.slide-enter-active,
.slide-leave-active{
  transition: all 1s ease;
}
.slide-enter,
.slide-leave-to {
  opacity: 0;
}

@media (max-width:737px){
  .routerContainer{
    padding-top: 5px;
  }
  .router-link-exact-active{
  color: rgb(211, 211, 211);
  border: none;
}
  .pages{
    font-size: 14px;
  }
}

@media (max-width:375px){
    .pages{
      font-size: 1rem;
    }
  }
</style>
