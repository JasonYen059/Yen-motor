<template>
    <div >
    <inputcom @tankimg="getimg"></inputcom>

    <div class="motor">
      <img class="engine" src="../../public/engine.png" width="400px" height="auto">
      <img  class="handle" src="../../public/handle.png" >
      
      <div class="motorbody">
        <svg id="motorbody" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 317.11 211.4"><path :d="mobody.url"/></svg>
      </div>
      
      <gastank :tankColor="motoritems[0].color" :tankX="motoritems[0].x" :tankY="motoritems[0].y" :showtank="gasid"></gastank>
      <seat  :seatX="motoritems[1].x" :seatY="motoritems[1].y" :showseat="seatid"></seat>  
      <sidecase :caseColor="motoritems[2].color" :caseX="motoritems[2].x" :caseY="motoritems[2].y" :showcase="caseid"></sidecase>
      <fork :forkColor="motoritems[3].color" :forkX="motoritems[3].x" :forkY="motoritems[3].y" :showfork="forkid"></fork>
      <wheels :showwheels="wheelsid"></wheels>
      <fender :fenderColor="motoritems[5].color" :fenderX="motoritems[5].x" :fenderY="motoritems[5].y" :showfender="fenderid"></fender>
      <light :lightColor="motoritems[6].color" :lightX="motoritems[6].x" :lightY="motoritems[6].y" :showlight="lightid"></light>
      <pipe :showpipe="pipeid"></pipe>

    </div>


  <button @click="turn()" class="colorchoose">
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 462.93 462.93">
      <g id="paint"><path d="M171.06,298h8.54v5.94c-7-.38-17.52-.66-17.54,9s10.56,9.38,17.54,9c0,7.28-1.82,20.11,9,20.12h52.56c5.93.06,9.73-5.46,9-11.08h27.53c-2,22.64-13.7,43-30.6,58.3-8.37,8.13,4.59,21.11,12.73,12.72,20.27-18.46,33.72-43.25,35.9-70.49a19.69,19.69,0,0,1,14.24,13l17.9,53.72a94.53,94.53,0,0,0,89.8,64.72c5.94.16,10.57-6.22,8.55-11.81l-50-151.73h21.13c11.67.17,11.67-18.18,0-18H367.48C357,267,330.26,271.6,315,271l11-31.55c5.18-3,61.42-13.57,61.28-21.75L440,54.39a9.06,9.06,0,0,0-5.8-11.33L302.15.44a9,9,0,0,0-11.33,5.8L238.11,169.49a9,9,0,0,0,1.49,8.33l35.27,44.86L258.07,271h-7.91c.72-5.62-3.06-11.13-9-11.08H188.6c-10.79,0-9,12.87-9,20.12h-8.54c-11.68-.17-11.67,18.18,0,18Zm249-240.56L416,70.16,301.07,33.06l4.11-12.73ZM319.2,222.63l-28.82-9.36-33.67-42.81L295.54,50.19l114.92,37.1L371.63,207.56ZM296,271H277.13l13.47-38.69,16.92,5.5ZM327,338.8A38.24,38.24,0,0,0,323.4,331h44.27l37.2,112.89C352.35,437.33,340.58,380.68,327,338.8ZM250.15,313V289h93.94c12.3-.81,14.55,15.53,17.65,24ZM197.6,277.87h34.56v46.18H197.6Z"/><path d="M24.06,382.47a9,9,0,0,0,12.51,2.39c1.51-2.78,123.34-78.95,116.49-83.9,7.31-4.71-115.43-81.27-116.49-83.89A9,9,0,1,0,26.45,232L128,301,26.45,370A9,9,0,0,0,24.06,382.47Z"/></g>
      <g id="paintcolor" :style="{fill:colorful}"><polygon points="295.54 50.19 410.46 87.29 371.63 207.56 319.2 222.63 290.38 213.27 256.71 170.46 295.54 50.19"/><polygon style="opacity:0.7;" points="26.45 231.96 128.04 300.96 26.45 369.97 26.45 231.96"/></g>
    </svg>
  </button>
  <div @click="choose" class="colordiv" v-show="showcolor" >
    <div class="circlediv" v-for="(colors,index) in circolor" :key="index" :style="{backgroundColor:colors.name}" :value="colors.name"></div>
  </div>
  
  <div id="controldir">
    <button class="way" @click="movel(imgtypefromchild)"><img class="dirbutton" src="../../public/left.png" ></button>
    <button class="way" @click="mover(imgtypefromchild)"><img class="dirbutton" src="../../public/right.png" ></button>
    <button class="way" @click="moveu(imgtypefromchild)"><img class="dirbutton" src="../../public/up.png" ></button>
    <button class="way" @click="moved(imgtypefromchild)"><img class="dirbutton" src="../../public/down.png" ></button>
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
      circolor:[{name:'red'},{name:'orange'},{name:'rgb(255, 220, 21)'},{name:'rgb(0, 128, 90)'},{name:'#000958'},{name:'white'},{name:'#c6cacc'},{name:'rgb(37, 37, 37)'}],
      

     mobody:{url:"M312,64.55,286.73,16.92a1.85,1.85,0,0,0-2.45-.79l-9.48,4.73a1.89,1.89,0,0,0-.86,2.53c.95,1.92,2.5,5.05,3.51,7a3.91,3.91,0,0,1-.87,4.88L177.43,70.05a6.21,6.21,0,0,1-2,.35l-167.67,0-1.2.3a2.06,2.06,0,0,0-.36,3.88L8,75.42C19.14,77.11,40.87,93,40.87,93l68.34,66.1a8.11,8.11,0,0,1,2,8.64c-1.56,4.25-3.25,10.56-4.61,16.07a9.41,9.41,0,0,0,9.07,11.67c14.24.1,36.77.23,40,0h86.66a11.7,11.7,0,0,0,11-7.72c9-25.06,37.06-102.75,38.8-107.44,2.08-5.6,6.8-5.87,6.8-5.87,2.37-3.12,8.92-6.08,12.14-7.39A1.8,1.8,0,0,0,312,64.55ZM66,82.36l65.35,0s4.71-.93,2.9,4.55-7.57,22.29-8.08,34.2.6,32.53,4.6,44.22l-71.69-71S49.92,82.35,66,82.36Zm211.39,8.5c-7.08,19.85-24,66.81-30.73,85.5a12,12,0,0,1-11.2,7.91l-75.29.31a14.19,14.19,0,0,1-13.62-10c-7-22.37-19.27-75.91,15.08-94.3a511.74,511.74,0,0,1,86.91-9.72S286.36,65.78,277.41,90.86Z",id:"1"}
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
  .engine {
    z-index: 2;
    position: absolute;
    left: 568px;
    top: 228px;
  }
  .handle{
    position: absolute;
    width: 220px;
    height: auto;
    top: 135px;
    left: 750px;
  } 
  .motorbody {
    width: 400px;
    height: auto;
    position: absolute;
    left: 548px;
    top: 226px;
    z-index: 1;
  }

  .darkzone{
    fill-opacity: 10%;
    fill: black;
  }

.fillsilver{
  fill: silver;
}

.fillblack{
  fill:black;
}


.colorchoose {
  width: 80px;
  height: 80px;
  background: none;
  border: none;
  border-radius: 100%;
  position: absolute;
  right: 40px;
  top: 130px;
  cursor: pointer;
}

.colordiv{
  width: 30px;
  display: flex;
  flex-direction: column;
  align-items: center;
  position: absolute;
  right: 55px;
  top: 220px;
}
.circlediv{
  width: 20px;
  height: 20px;
  border: 1px solid rgb(143, 143, 143);
  border-radius: 50%;
  margin: 10px;
  float: left;
  cursor: pointer;
}

#controldir {
  position: absolute;
  right: 100px;
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
  opacity: 0.5;
  cursor: pointer;
  transition: all 0.5s;
}
.dirbutton:hover {
  opacity: 1;
}

</style>