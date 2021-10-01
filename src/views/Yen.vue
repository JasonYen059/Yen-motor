<template>
  <div class="custom">
  
    <div class="motorcontainer">

      <div class="itembar">
        <inputcom @tankimg="getimg"></inputcom>
      </div>
      
      <div class="motor">
        <motorbody></motorbody>
        <engine></engine>
        <handle></handle>
        <gastank :tankColor="motoritems[0].color" :tankX="motoritems[0].x" :tankY="motoritems[0].y" :showtank="gasid"></gastank>
        <seat  :seatX="motoritems[1].x" :seatY="motoritems[1].y" :showseat="seatid"></seat>  
        <sidecase :caseColor="motoritems[2].color" :caseX="motoritems[2].x" :caseY="motoritems[2].y" :showcase="caseid"></sidecase>
        <fork :forkColor="motoritems[3].color" :forkX="motoritems[3].x" :forkY="motoritems[3].y" :showfork="forkid"></fork>
        <wheels :showwheels="wheelsid"></wheels>
        <fender :fenderColor="motoritems[5].color" :fenderX="motoritems[5].x" :fenderY="motoritems[5].y" :showfender="fenderid"></fender>
        <light :lightColor="motoritems[6].color" :lightX="motoritems[6].x" :lightY="motoritems[6].y" :showlight="lightid"></light>
        <pipe :showpipe="pipeid"></pipe>
      </div>


      <div class="controlbar">
        <button @click="turn()" class="colorchoose">
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 462.93 462.93">
            <g id="paint"><path d="M171.06,298h8.54v5.94c-7-.38-17.52-.66-17.54,9s10.56,9.38,17.54,9c0,7.28-1.82,20.11,9,20.12h52.56c5.93.06,9.73-5.46,9-11.08h27.53c-2,22.64-13.7,43-30.6,58.3-8.37,8.13,4.59,21.11,12.73,12.72,20.27-18.46,33.72-43.25,35.9-70.49a19.69,19.69,0,0,1,14.24,13l17.9,53.72a94.53,94.53,0,0,0,89.8,64.72c5.94.16,10.57-6.22,8.55-11.81l-50-151.73h21.13c11.67.17,11.67-18.18,0-18H367.48C357,267,330.26,271.6,315,271l11-31.55c5.18-3,61.42-13.57,61.28-21.75L440,54.39a9.06,9.06,0,0,0-5.8-11.33L302.15.44a9,9,0,0,0-11.33,5.8L238.11,169.49a9,9,0,0,0,1.49,8.33l35.27,44.86L258.07,271h-7.91c.72-5.62-3.06-11.13-9-11.08H188.6c-10.79,0-9,12.87-9,20.12h-8.54c-11.68-.17-11.67,18.18,0,18Zm249-240.56L416,70.16,301.07,33.06l4.11-12.73ZM319.2,222.63l-28.82-9.36-33.67-42.81L295.54,50.19l114.92,37.1L371.63,207.56ZM296,271H277.13l13.47-38.69,16.92,5.5ZM327,338.8A38.24,38.24,0,0,0,323.4,331h44.27l37.2,112.89C352.35,437.33,340.58,380.68,327,338.8ZM250.15,313V289h93.94c12.3-.81,14.55,15.53,17.65,24ZM197.6,277.87h34.56v46.18H197.6Z"/><path d="M24.06,382.47a9,9,0,0,0,12.51,2.39c1.51-2.78,123.34-78.95,116.49-83.9,7.31-4.71-115.43-81.27-116.49-83.89A9,9,0,1,0,26.45,232L128,301,26.45,370A9,9,0,0,0,24.06,382.47Z"/></g>
            <g id="paintcolor" :style="{fill:colorful}"><polygon points="295.54 50.19 410.46 87.29 371.63 207.56 319.2 222.63 290.38 213.27 256.71 170.46 295.54 50.19"/><polygon style="opacity:0.7;" points="26.45 231.96 128.04 300.96 26.45 369.97 26.45 231.96"/></g>
          </svg>
        </button>

        <div @click="choose" class="colordiv" v-show="showcolor" >
              <div class="circlediv" v-for="(colors,index) in circolor" :key="index" :style="{backgroundColor:colors.name}" :value="colors.name"></div>
        </div>

        <div class="controldir" style="background-image: url('way.png'); background-size: cover;">
            <div class="lrway">
              <button class="way" @click="movel(imgtypefromchild)"><img class="dirbutton " src="../../public/left.png" ></button>
            </div>
            <div class="midway">
              <button class="way" @click="moveu(imgtypefromchild)"><img class="dirbutton " src="../../public/up.png" ></button>
              <button class="way" @click="moved(imgtypefromchild)"><img class="dirbutton " src="../../public/down.png" ></button>
            </div>
            <div class="lrway">
              <button class="way" @click="mover(imgtypefromchild)"><img class="dirbutton " src="../../public/right.png" ></button>
            </div>
            
            
        </div>

      </div>
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
import motorbody from '@/components/Motorbody.vue'
import engine from '@/components/Engine.vue'
import handle from '@/components/Handle.vue'

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
    light,
    motorbody,
    engine,
    handle
  },
  computed:{
  },
  methods:{
    turn(){
      this.showcolor= !this.showcolor
    },
    choose: function(event){
      console.log(event)
      this.colorful = event.srcElement.attributes[0].value
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
      
    }
  }
}
</script>

<style >
  .custom{
    width: 100%;
    height: 100%;
    background-color: #3f3f3f;
    position: absolute;
    top: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
  }

  .motorcontainer {
    width: 100%;
    height: 80%;
    position: relative;
    display: flex;
    align-items: center;
    background-image: url('../../public/workshop1.png'); 
    background-size: cover;
  }

  .itembar{
    width: 20%;
    height: 100%;
  }

  .motor {
    position: relative;
    width: 80vw;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .controlbar{
    width: 15%;
    height: 100%;
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding-top: 1%;
    z-index: 15;
  }

  .darkzone{
    fill-opacity: 10%;
    fill: black;
  }

.colorchoose {
  width: 75px;
  height: auto;
  background: none;
  border: none;
  cursor: pointer;
}

.colordiv{
  width: 30px;
  display: flex;
  flex-direction: column;
  align-items: center;
  
}
.circlediv{
  width: 20px;
  height: 20px;
  border: 1px solid rgb(143, 143, 143);
  border-radius: 50%;
  margin: 10px;
  cursor: pointer;
}

.controldir {
  position: absolute;
  bottom: 5%;
  width: 120px;
  height: 120px;
  opacity: 0.3;
  display: flex;
  align-items: center;
  z-index: 15;
}
.lrway{
  width: 33%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  
}
.midway{
  width: 33%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding-top: 5px;
}
.way {
  background: none;
  border: none;
  margin: 5px;
}

.dirbutton {
  width:35px;
  height:auto;
  border-radius: 100%;
  border: none;
  cursor: pointer;
  transition: all 0.5s;
  position: relative;
}
.controldir:hover {
  opacity: 0.6;
}


@media (max-width:1200px) {
    .motorcontainer{
      flex-direction: column;
    }
    .itembar{
      width: 100%;
      height: 20%;
    }
    .motor {
      width: 100%;
    }
    .controlbar{
      position: absolute;
      bottom: 0;
      width: 100%;
      height: 20%;
      flex-direction: row;
      justify-content:start;
      padding-left: 6%;
    }
    .colorchoose{
      width:60px;
    }
    .colordiv{
      width: 400px;
      flex-direction: row;
      margin-left: 25%;
    }
    .controldir{
      right: 2%;
      width: 90px;
      height: 90px;
    }
    .dirbutton{
      width: 20px;
    }
    
  }

  @media (max-width:768px){
    .motorcontainer{
      background-image: url('../../public/workshop768.png'); 
      height: 85%;
    }
    .itembar{
      height: 30%;
    }
    .motor {
      height: 60%;
    }
    .colordiv{
      margin-left: 15%;
    }
  }

  @media (max-width:736px){
    .motorcontainer{
      background-image: url('../../public/workshop736.png'); 
    }
    .motor {
      height: 80%;
    }
    .colorchoose{
      width:35px;
    }
    .colordiv{
      margin-left: 20%;
      margin-top: 15px;
    }
    .circlediv{
      width: 15px;
      height: 15px;
    }
    .libar{
      line-height: 40px;
      height: 40px;
    }
  }

  @media (max-width:415px){
    .motor {
      height: 55%;
    }
    .controlbar{
      height: 10%;
    }
    .colordiv{
      margin-left: 10%;
    }
    .circlediv{
      width: 15px;
      height: 15px;
      margin: 5px;
    }
    .colorchoose{
      width:40px;
    }
    .controldir{
      width: 60px;
      height: 60px;
    }
  }

  
</style>