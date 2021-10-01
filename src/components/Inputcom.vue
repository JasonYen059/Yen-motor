<template>

<div id="itemselect">
    <ul class="ulbar1">
        <transition name="fixfade">
            <button class="fix" @click="fixmotor"><span><i class="fas fa-wrench"></i></span></button>
        </transition>

        <li class="libar1"  v-for="(item,index) of selectbar" :key="item.id"  @click="choseone(item.id)">
            <span v-show="item.id == typeid" class="triangle"><i class="fas fa-caret-right"></i></span>
            <p :class="{ active: item.id == typeid }" class="itemtype">{{item.name}}</p> 
            <transition-group name="fade" tag="div">
            <div id="divbar" v-show="item.id == typeid" :key="item.id">
                <ul class="ulbar2" :key="item.id">
                    <li class="libar2" :class="{ imgactive: img.num == imgnum }" v-for="img of selectbar[index].imgs" :key="img.num" @click="choseimg(img.num)">
                        <img class="pngs" :src="img.img" width="80px" height="auto">
                        <input class="numinput" @blur="numout" v-model="inputnumber" v-show="img.num == 9 | img.num == 10 " type="text" placeholder="Num">
                        <div class="twocolorbar" v-show="img.num == 9 | img.num == 10 ">
                            <button @click="numblack" class="colorstick blackstick"></button>
                            <button @click="numwhite" class="colorstick whitestick"></button>
                        </div>
                        <div class="twocolorbar" v-show="img.num == 5 | img.num == 6 | img.num == 7">
                            <button @click="seatblack" class="colorstick blackstick"></button>
                            <button @click="seatbrown" class="colorstick brownstick"></button>
                        </div>
                    </li>
                </ul>
            </div>
            </transition-group> 
        </li>
        
    </ul>
    
</div>
   
</template>


<script>
import {bus} from '../main';
export default {
    name:"inputcom",
    data(){
        return{
            typeid:0,
            imgnum:0,
            selectbar:[
                {name:"Tank",imgs:[{img:'tank1.png',num:1},{img:'tank2.png',num:2},{img:'tank3.png',num:3},{img:'tank4.png',num:4}],id:1},
                {name:"Seat",imgs:[{img:'seat1.png',num:5},{img:'seat2.png',num:6},{img:'seat3.png',num:7}],id:2},
                {name:"Case",imgs:[{img:'case1.png',num:8},{img:'case2.png',num:9},{img:'case3.png',num:10}],id:3},
                {name:"Forks",imgs:[{img:'forks1.png',num:11},{img:'forks2.png',num:12},{img:'forks3.png',num:13}],id:4},
                {name:"Wheels",imgs:[{img:'wheels1.png',num:14},{img:'wheels2.png',num:15},{img:'wheels3.png',num:16}],id:5},
                {name:"Fender",imgs:[{img:'fender1.png',num:17},{img:'fender2.png',num:18}],id:6},
                {name:"Light",imgs:[{img:'light1.png',num:19},{img:'light2.png',num:20}],id:7},
                {name:"Pipe",imgs:[{img:'pipesmall1.png',num:21},{img:'pipesmall2.png',num:22}],id:8}
                ],
            inputnumber:'',
            numbercolor:'',
            showlist: false
           
        }
    },
    props:{},
    
    methods:{
        choseone:function(e){
            this.typeid = e
        },
        choseimg:function(e){
            this.imgnum = e
            this.$emit('tankimg',this.typeid,this.imgnum)
        },
        numout(){
            bus.$emit('caseinfo',this.inputnumber)
        },
        numwhite(){
            this.numbercolor = "white"
            bus.$emit('numcolor',this.numbercolor)
        },
        numblack(){
            this.numbercolor = "black"
            bus.$emit('numcolor',this.numbercolor)
        },
        seatblack(){
            bus.$emit('seatcolor','#2e2e2e')
        },
        seatbrown(){
            bus.$emit('seatcolor','rgb(116, 66, 1)')
        },
        fixmotor(){
            this.typeid = 0
            // this.showlist = !this.showlist
        }

    }
    
}
</script>

<style scoped>
#itemselect {
    width: 100%;
    height: 100%;
    background: none;
    transition: all 1s ease;
}

.ulbar1 {
    list-style: none;
    color: #e6e6e6;
    position: relative;
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
}

.ulbar2 {
    list-style: none;
    margin: auto;
    color: #e6e6e6;
}

.libar1 {
    font-size: 2vw;
    font-weight: 700;
    height: 4vw;
    width: 130px;
    line-height: 60px;
    text-align: center;
    cursor: pointer;
    border-radius: 10px;
    display: flex;
    position: relative;
}
.libar2 {
    width: 85px;
    height: 85px;
    background:none;
    border-radius: 10px;
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin: 5px;
    z-index: 15;
    }

#divbar {
    border-radius: 10px;
    position: relative;
    top: -5vw;
    margin-left: 60px;
    border:5px solid rgb(165, 165, 165);
    background-color: #f5f5f5;
    display: flex;
    justify-content: center;
    
}
.itemtype{
    opacity: 0.3;
    margin-left: 3.5vw;
    width: 9vw;
}
.itemtype:hover{
    opacity: 0.8;
}
.active {
    color: #ffffff;
    opacity: 1;
}
.imgactive {
    background-color: rgb(230, 230, 230);
}

.numinput {
    width: 54%;
    height: 25%;
    border: none;
    background: none;
    text-align: center;
    position: absolute;
    top: 30%;
    left: 22%;
    font-size: 1.5rem;
    font-family: 'Lobster', cursive;
    line-height: 21px;
}
::placeholder{
    font-size: 17px;
    color: rgb(167, 167, 167);
}

.colorstick{
    width: 20px;
    height: 8px;
    margin: 0 3px 0 3px;
    border: 1px solid rgb(85, 85, 85);
    border-radius: 3px;
    transition: all 0.5s;
}
.colorstick:hover {
    width: 25px;
    height: 10px;
}

.blackstick{
    background-color: black;
}
.whitestick {
    background-color: white;
}
.brownstick {
    background-color: rgb(161, 91, 0);
}
.twocolorbar{
    width: 100%;
    height: 15px;
    display: flex;
    justify-content: center;
    margin-bottom: 5px;
}
.triangle{
    position: absolute;
    margin: 0 1vw;
    
}
.fix {
    width: 130px;
    height: 60px;
    background: none;
    border: none;
    font-size: 3vw;
    color: #f5f5f5;
    cursor: pointer;
    margin: 1vw 2vw;
}
.fix span{
    width: 40px;
    height: 40px;
    margin: auto;
}
.fade-enter-active, 
.fade-leave-active,
.fixfade-enter-active,
.fixfade-leave-active {
  transition: all .5s ease;
}

.fade-enter,
.fixfade-enter {
  transform: translateX(-50px);
  opacity: 0;
}

.fade-leave-to,
.fixfade-leave-to {
  transform: scale(0);
  opacity: 0;
}
/* ----------------------------------------1200---------------------------------------- */
@media (max-width:1200px) {
    .ulbar1{
        display: flex;
        flex-direction: row;
        justify-content: center;
        color: rgb(65, 65, 65);
        padding-top: 10px;
    }
    .active {
        color: #383838;
        opacity: 1;
    }
    .libar1{
        font-size: 22px;
        width: 10%;
    }
    .ulbar2{
        display: flex;
        flex-direction: row;
    }
   #divbar {
       margin-left: 0;
       position: absolute;
       left: 0;
       top: 6vh;
       margin-top: 10px;
   }
   .libar2 {
       width: 60px;
       height: 60px;
   }
   .fix {
       color:rgb(133, 133, 133);
       width: 2vw;
       margin: 0;
   }
   .triangle{
       left: 0;
       display: none;
   }
   .numinput{
       font-size: 20px;
   }
   .itemtype{
       margin-left: 30px;
   }
}
/* ----------------------------------------------768----------------------------------- */
@media (max-width:768px){
    #divbar{
        left: 23%;
    }
    .ulbar1{
      color: #e6e6e6;
      justify-content:left;
    }
    .active {
    color: #ffffff;
}
    .libar1{
        font-size: 24px;
        width: auto;
    }
    .itemtype{
        margin-left: 25px;
    }
    .triangle{
        display: none;
    }
    .ulbar2{
        flex-direction: column;
    }
    .fade-enter,.fixfade-enter {
        transform: translateY(-50px);
        opacity: 0;
    }
/* --------------------------------------736--------------------------------- */
    @media (max-width:736px){
        .ulbar1{
            padding-top: 0;
        }
        .ulbar2{
            flex-direction: row;
        }
        #divbar{
            margin-top: 0;
        }
        .libar1{
            font-size: 15px;
        }
        .itemtype{
        margin-left: 35px;
        }
        .libar2{
            width: 40px;
            height: 40px;
        }
        .fix{
            font-size: 25px;
        }
        
    }
/* ---------------------------------------------420------------------------------------------ */
    @media (max-width:420px){
        #divbar{
            height: 100px;
            overflow: scroll;
        }
        .ulbar1{
            overflow: scroll;
        }
        .libar1{
            margin: 0 10px;
        }
  }
}

</style>