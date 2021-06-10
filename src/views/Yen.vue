<template>
    <div >
    <inputcom @tankimg="getimg"></inputcom>
    <div class="motor">
      <img src="../../public/engine.png" width="400px" height="auto">

      <div class="motorbody">
        <svg id="motorbody" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 317.11 211.4"><path :d="mobody[0].url"/></svg>
      </div>
      
      <gastank :tankColor="motoritems[0].color" :tankX="motoritems[0].x" :tankY="motoritems[0].y" :showtank="gasid"></gastank>
      <seat  :seatX="motoritems[1].x" :seatY="motoritems[1].y" :showseat="seatid"></seat>  
      <sidecase :caseColor="motoritems[2].color" :caseX="motoritems[2].x" :caseY="motoritems[2].y" :showcase="caseid"></sidecase>
      <fork :forkColor="motoritems[3].color" :forkX="motoritems[3].x" :forkY="motoritems[3].y" :showfork="forkid"></fork>
      <wheels :showwheels="wheelsid"></wheels>
      <fender :fenderColor="motoritems[5].color" :fenderX="motoritems[5].x" :fenderY="motoritems[5].y" :showfender="fenderid"></fender>
      <light :lightColor="motoritems[6].color" :lightX="motoritems[6].x" :lightY="motoritems[6].y" :showlight="lightid"></light>
      <pipe :showpipe="pipeid"></pipe>

      
      <div class="handle">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 105.7 98.81"><g id="handlesilver" class="fillsilver"><path  d="M62,42.45s7.08-3.05,12.27,4.43S83.43,60,86.52,69.7a10.64,10.64,0,0,1-7.78,4.07s-9.47-22.08-16.5-22.46C62.24,51.31,60.28,44.92,62,42.45Z"/></g><g id="handle"><path  d="M49.5,36.91s5.68-2.1,9.66,2.34c0,0,2.9,2.47,3,4.56s.67,7.36-1.38,8.77-4.8,5.5-10.38,3.88-2.3-4.23-23-4c0,0,5.18-5,.12-11.44l13.16-.21S47.94,39.15,49.5,36.91Z"/></g><g id="handleblack" class="fillblack"><path d="M48.86,36.78a1.9,1.9,0,0,1,1.09.59c1.21,1.35,4.49,5.22,4.88,8.16a9.93,9.93,0,0,1-1.76,6.61s-.57.93-1.61,2.32c-.49.67-1.76,2-2.59,2.1-3.33.22-11,.29-11.24-3.72,0,0-5.84-1.41-10.23-.44,0,0-8.67,2.22-9.77-4.38s3.82-7.19,4.86-7.22,5,.16,5,.16,2.37,3.1,2.38,5.75a8.55,8.55,0,0,1-2.48,5.64s3.25-1.12,10.25.31c0,0,.69-.39,3.64,0a11.79,11.79,0,0,0,5.46-.56,5.94,5.94,0,0,0,3.75-5.37,5.44,5.44,0,0,0-2.94-5.39,12.09,12.09,0,0,0-5.88-.74c-2.76.53-4.24.59-4.51.2C37.19,40.84,38.41,35.11,48.86,36.78Z"/></g><g id="handledark" class="darkzone"><path  d="M59.61,53.56c-3.63,3.18-5.7,3.16-5.7,3.16s-14.29-.81-16.36-3-10.13-1.39-10.13-1.39l2.48-5.64,32.38.14L62.21,51s3.52-3,9.88,5.62l8.42,16.91-1.77.22S68.52,50.87,62,51.51Z"/></g></svg>
      </div>
    </div>


  <button @click="turn()" class="colorchoose">color</button>
  <div @click="choose" class="colordiv" v-show="showcolor" >
    <div class="circlediv" v-for="(colors,index) in circolor" :key="index" :style="{backgroundColor:colors.name}" :value="colors.name"></div>
  </div>
  
  <div id="controldir">
    <button class="way" @click="movel(imgtypefromchild)"><img class="dirbutton" src="left.png" ></button>
    <button class="way" @click="mover(imgtypefromchild)"><img class="dirbutton" src="right.png" ></button>
    <button class="way" @click="moveu(imgtypefromchild)"><img class="dirbutton" src="up.png" ></button>
    <button class="way" @click="moved(imgtypefromchild)"><img class="dirbutton" src="down.png" ></button>
  </div>
  
    </div>
</template>

<script>
import inputcom from '@/components/Inputcom.vue'
import sidecase from '@/components/Sidecase.vue'
import gastank from '@/components/Gastank.vue'
import seat from '@/components/Seat.vue'
import fork from '@/components/Fork.vue'
import pipe from '@/components/Pipe.vue'
import wheels from '@/components/Wheels.vue'
import fender from '@/components/Fender.vue'
import light from '@/components/Light.vue'

export default {
  components:{
    inputcom,
    sidecase,
    gastank,
    seat,
    fork,
    pipe,
    wheels,
    fender,
    light
  },
  computed:{
  },
  methods:{
    turn(){
      this.showcolor= !this.showcolor
    },
    choose: function(event){
      this.colorful = event.srcElement.attributes[1].value
      this.motoritems[this.imgtypefromchild-1].color = this.colorful
    },
    mover: function(type){
      this.motoritems[type-1].x = this.motoritems[type-1].x+2
    },
    movel: function(type){
      this.motoritems[type-1].x = this.motoritems[type-1].x-2
    },
    moveu: function(type){
      this.motoritems[type-1].y = this.motoritems[type-1].y-2
    },
    moved: function(type){
      this.motoritems[type-1].y = this.motoritems[type-1].y+2
    },
    getimg(imgtype,imgid){
      this.imgtypefromchild = imgtype
      if(imgtype == 1 ){
        this.gasid = imgid
      }else if (imgtype == 2){
        this.seatid = imgid
      }else if(imgtype == 3) {
        this.caseid = imgid
      }else if(imgtype == 4) {
        this.forkid = imgid
      }else if (imgtype == 5){
        this.wheelsid = imgid
      }else if (imgtype == 6){
        this.fenderid = imgid
      }else if (imgtype == 7){
        this.lightid = imgid
      }else {
        this.pipeid = imgid
      }
    },
    
    
  },
  data(){
    return{
      motoritems:[
        {id:'1',item:'gastank',color:'orange',x:0,y:0},
        {id:'2',item:'seat',color:'orange',x:0,y:0},
        {id:'3',item:'case',color:'orange',x:0,y:0},
        {id:'4',item:'fork',color:'orange',x:0,y:0},
        {id:'5',item:'wheels',color:'silver',x:0,y:0},
        {id:'6',item:'fender',color:'orange',x:0,y:0},
        {id:'7',item:'light',color:'orange',x:0,y:0},
        {id:'8',item:'pipe',color:'',x:0,y:0}
      ]
      ,
      imgtypefromchild:0,
      gasid:1 ,
      seatid:6,
      caseid:8,
      forkid:11,
      wheelsid:14,
      fenderid:17,
      lightid:19,
      pipeid:21,
      colorful:'',
      showcolor:false,
      circolor:[{name:'red'},{name:'orange'},{name:'yellow'},{name:'rgb(0, 128, 90)'},{name:'rgb(37, 37, 37)'},{name:'silver'},{name:'#000958'}],
      

     mobody:[{url:"M312,64.55,286.73,16.92a1.85,1.85,0,0,0-2.45-.79l-9.48,4.73a1.89,1.89,0,0,0-.86,2.53c.95,1.92,2.5,5.05,3.51,7a3.91,3.91,0,0,1-.87,4.88L177.43,70.05a6.21,6.21,0,0,1-2,.35l-167.67,0-1.2.3a2.06,2.06,0,0,0-.36,3.88L8,75.42C19.14,77.11,40.87,93,40.87,93l68.34,66.1a8.11,8.11,0,0,1,2,8.64c-1.56,4.25-3.25,10.56-4.61,16.07a9.41,9.41,0,0,0,9.07,11.67c14.24.1,36.77.23,40,0h86.66a11.7,11.7,0,0,0,11-7.72c9-25.06,37.06-102.75,38.8-107.44,2.08-5.6,6.8-5.87,6.8-5.87,2.37-3.12,8.92-6.08,12.14-7.39A1.8,1.8,0,0,0,312,64.55ZM66,82.36l65.35,0s4.71-.93,2.9,4.55-7.57,22.29-8.08,34.2.6,32.53,4.6,44.22l-71.69-71S49.92,82.35,66,82.36Zm211.39,8.5c-7.08,19.85-24,66.81-30.73,85.5a12,12,0,0,1-11.2,7.91l-75.29.31a14.19,14.19,0,0,1-13.62-10c-7-22.37-19.27-75.91,15.08-94.3a511.74,511.74,0,0,1,86.91-9.72S286.36,65.78,277.41,90.86Z",id:"1"}]
    }
  }
}
</script>

<style scoped>
  .motor {
    margin-top: 48px;
    background-color: #f5f5f5;
    width: 100%;
    min-height: 80vh;
    display: flex;
    justify-content: center;
    align-items: center;
    
  }
  img {
    z-index: 2;
    position: absolute;
  }
  #motorbody {
    width: 400px;
    height: auto;
  }
  .motorbody {
    position: relative;
    left: -20px;
    top: -1px;
    z-index: 1;
  }
  .case {
    position: absolute;
  }

  .darkzone{
    fill-opacity: 10%;
    fill: black;
  }

  .lightzone{
    fill: #fff;
    fill-opacity: 40%;
  }

.fillsilver{
  fill: silver;
}

.fillblack{
  fill:black;
}

.handle {
  position: absolute;
  width: 150px;
  top: 143px;
  right: 610px;
}
#handle{
  fill: grey;
}

#others {
  position: absolute;
  width: 850px;
  top: 165px;
  right: 330px;
  z-index: 1;
}
.colorchoose {
  width: 50px;
  height: 50px;
  text-align: center;
  border-radius: 100%;
  position: absolute;
  right: 20px;
  top: 200px;
}
.colordiv{
  width: 30px;
  display: flex;
  flex-direction: column;
  align-items: center;
  position: absolute;
  right: 30px;
  top: 260px;
}
.circlediv{
  width: 20px;
  height: 20px;
  border-radius: 50%;
  margin: 10px;
  float: left;
}

#controldir {
  position: absolute;
  right: 50px;
  bottom: 50px;
  width: 150px;
  height: 150px;
  z-index: 10;
  display: flex;
  justify-content: space-around;
  align-items: center;
}
.way {
  background: none;
  border: none;
}

.dirbutton {
  width:50px;
  height:auto;
  opacity: 50%;
  cursor: pointer;
  transition: all 0.5s;
}
.dirbutton:hover {
  opacity: 90%;
}

</style>