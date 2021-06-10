<template>
<div id="itemselect">
    <ul class="ulbar1">
        <li class="libar1" :class="{ active: item.id == typeid }" v-for="(item,index) of selectbar" :key="item.id"  @click="choseone(item.id)">
            {{item.name}}
            <div id="divbar" v-show="item.id == typeid">
                <ul class="ulbar1">
                    <li class="libar2" :class="{ imgactive: img.num == imgnum }" v-for="img of selectbar[index].imgs" :key="img.num" @click="choseimg(img.num)">
                        {{img.img}}
                        <input class="numinput" @blur="numout" v-model="inputnumber" v-show="img.num == 9 | img.num == 10 " type="text" placeholder="Number">
                        <div v-show="img.num == 9 | img.num == 10 ">
                            <button @click="numblack" class="colorstick blackstick"></button>
                            <button @click="numwhite" class="colorstick whitestick"></button>
                        </div>
                        <div v-show="img.num == 5 | img.num == 6 | img.num == 7">
                            <button @click="seatblack" class="colorstick blackstick"></button>
                            <button @click="seatbrown" class="colorstick brownstick"></button>
                        </div>
                    </li>
                </ul>
            </div>
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
                {name:"Tank",imgs:[{img:'Tank1',num:1},{img:'Tank2',num:2},{img:'Tank3',num:3},{img:'Tank4',num:4}],id:1},
                {name:"Seat",imgs:[{img:'Seat1',num:5},{img:'Seat2',num:6},{img:'Seat3',num:7}],id:2},
                {name:"Case",imgs:[{img:'Case1',num:8},{img:'Case2',num:9},{img:'Case3',num:10}],id:3},
                {name:"Forks",imgs:[{img:'Fork1',num:11},{img:'Fork2',num:12},{img:'Fork3',num:13}],id:4},
                {name:"Wheels",imgs:[{img:'wheels1',num:14},{img:'wheels2',num:15},{img:'wheels3',num:16}],id:5},
                {name:"Fender",imgs:[{img:'Fender1',num:17},{img:'Fender2',num:18}],id:6},
                {name:"Light",imgs:[{img:'light1',num:19},{img:'light2',num:20}],id:7},
                {name:"Pipe",imgs:[{img:'pipe1',num:21},{img:'pipe2',num:22}],id:8}
                ],
            isActive:false,
            inputnumber:'',
            numbercolor:''
           
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
        }

    }
    
}
</script>

<style scoped>
#itemselect {
    position: absolute;
    top: 120px;
    left: 20px;
    width: 130px;
    height: 480px;
    background-color: #e0e0e0;
    border-radius: 10px;
}

.ulbar1 {
    list-style: none;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.libar1 {
    font-size: 20px;
    height: 60px;
    width: 130px;
    line-height: 60px;
    text-align: center;
    border-bottom: 2px solid grey ;
    cursor: pointer;
    border-radius: 10px 0 0 10px;
}
.libar1:last-child{
    border: none;
}

.libar2 {
    width: 130px;
    background-color:rgb(252, 203, 67) ;
    }

#divbar {
    position: relative;
    top: -60px;
    right: -130px;
    background-color: rgb(240, 240, 240);
}
.active {
    background-color: rgb(252, 203, 67);
}
.imgactive {
    background-color: rgb(252, 222, 140);
}
.numinput {
    width: 60px;
    height: 30px;
    border: none;
    background: none;
    text-align: center;
}
::placeholder{
    color: rgb(167, 167, 167);
}

.colorstick{
    width: 20px;
    height: 8px;
    margin: 0 3px 0 3px;
    border: none;
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
</style>