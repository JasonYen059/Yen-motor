<template>
<div id="itemselect">
    <ul class="ulbar1">
        <li class="libar1" :class="{ active: item.id == typeid }" v-for="(item,index) of selectbar" :key="item.id"  @click="choseone(item.id)">
            <span v-show="item.id == typeid" class="triangle"><i class="fas fa-caret-right"></i></span>
            <p>{{item.name}}</p> 
            <div id="divbar" v-show="item.id == typeid">
                <ul class="ulbar1">
                    <li class="libar2" :class="{ imgactive: img.num == imgnum }" v-for="img of selectbar[index].imgs" :key="img.num" @click="choseimg(img.num)">
                        <img class="pngs" :src="img.img" width="80px" height="auto">
                        <input class="numinput" @blur="numout" v-model="inputnumber" v-show="img.num == 9 | img.num == 10 " type="text" placeholder="Number">
                        <div class="colordiv" v-show="img.num == 9 | img.num == 10 ">
                            <button @click="numblack" class="colorstick blackstick"></button>
                            <button @click="numwhite" class="colorstick whitestick"></button>
                        </div>
                        <div class="colordiv" v-show="img.num == 5 | img.num == 6 | img.num == 7">
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
    top: 110px;
    left: 20px;
    width: 130px;
    height: 480px;
    background: none;
    border-radius: 10px;
    transition: all 1s ease;
}

.ulbar1 {
    list-style: none;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.libar1 {
    font-size: 25px;
    font-weight: 700;
    height: 60px;
    width: 130px;
    line-height: 60px;
    text-align: center;
    cursor: pointer;
    border-radius: 10px;
}
.libar2 {
    width: 85px;
    height: 85px;
    background:none;
    border-radius: 10px;
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 5px;
    }

#divbar {
    width: 110px;
    border-radius: 10px;
    padding: 5px;
    position: relative;
    top: -80px;
    right: -140px;
    border:5px solid gray;
    background-color: #f5f5f5;
}
/* .active {
    background-color: rgb(231, 231, 231);
} */
.imgactive {
    background-color: rgb(230, 230, 230);
}

.numinput {
    width: 45px;
    height: 25px;
    border: none;
    background: none;
    text-align: center;
    position: absolute;
    top: 30px;
    left: 21px;
    font-size: 20px;
    font-family: 'Lobster', cursive;
}
::placeholder{
    font-size: 15px;
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
.colordiv{
    position: absolute;
    top: 43px;
    left: 18px;
}
.triangle{
    position: absolute;
    left: 0;
}
</style>