<template >
<div id="casediv" class="motorset"> 
    <svg v-show="showcase == 8" id="case" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 779.53 425.2">
        <svg :x="caseX" :y="caseY">
            <g id="case1" :style="{fill:caseColor}"><path d="M283.67,185.62c-6.91-6.75-13.86-13.47-20.73-20.28-1.91-1.89-4.19-5.17-2.62-8,1.46-2.6,3.87-3.64,7.45-3.61,17.78.18,35.57.17,53.35.22a1.93,1.93,0,0,1,1.63.88,23.21,23.21,0,0,1,2.35,6,17.18,17.18,0,0,1,.31,7.21,71.69,71.69,0,0,1-1.75,8.23c-2,6.38-4,10.12-12.6,9.72C302,185.59,292.8,185.7,283.67,185.62Zm36.43-29.76"/></g>
            <g id="caselight1" class="lightzone"><path d="M321.48,157.09l-55.43.54c.86-2.33,2.47-2.12,4-2.12h49.29C320,155.55,321.48,155.28,321.48,157.09Z"/></g>
            <g id="casedark1" class="darkzone"><path d="M325.41,168a74.48,74.48,0,0,1-1.76,8.24c-2,6.38-4,10.12-12.6,9.72-9.11-.44-18.26-.33-27.39-.41-6.91-6.75-13.86-13.47-20.73-20.28a8.85,8.85,0,0,1-2.65-4c-.51,2.25,1,4.14,2.65,5.73,6.87,6.81,13.82,13.53,20.73,20.28,9.13.08,18.28,0,27.39.41,8.6.4,10.6-3.34,12.6-9.72a73.8,73.8,0,0,0,1.76-8.23,17.11,17.11,0,0,0,.21-3.78A15.05,15.05,0,0,1,325.41,168Z"/><path d="M320.48,179.27c-1,3.19-3.69,5.12-7.74,5.15-7.8.05-15.6,0-23.4,0-3.66,0-6-2.21-8.94-4.16C294.93,180.65,302.2,182.52,320.48,179.27Z"/></g>
        </svg> 
    </svg>  

    <div class="numberdiv">
    <svg  v-show="showcase == 9" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 779.53 425.2">
        <svg :x="caseX" :y="caseY">
            <g id="seccolor" style="fill:#fff;stroke:#666;stroke-width:0.25px;"><ellipse class="cls-1" cx="298.07" cy="182.7" rx="44.86" ry="36"/></g>
            <g id="maincolor" :style="{fill:caseColor,stroke:strokecolor}"><ellipse class="cls-2" cx="298.07" cy="182.7" rx="41.75" ry="33.5"/></g>
            <g id="darkzone" class="darkzone"><path d="M343,184c0,19.88-20.09,36.79-44.86,36.79S253.24,203.88,253.24,184c0,0,3.07,34.39,44.87,34.39S343,184,343,184Z"/><path  d="M264.14,163.72c10.94-13.3,29.32-14.52,33.93-14.52,9.75,0,27.5,4.54,34,14.61,0,0-11-12.78-34-12.78A52.32,52.32,0,0,0,264.14,163.72Z"/></g>
        </svg>
     </svg>
     <p v-if="showcase == 9" :style="{color:numbercolor,left:numleft,top:numtop}" >{{customnum}}</p>
     </div>


    <div class="numberdiv">
    <svg  v-show="showcase == 10" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 779.53 425.2">
        <svg :x="caseX" :y="caseY">
            <g id="seccolor" style="fill:#fff;stroke:#666;stroke-width:0.25px;"><rect class="cls-1" x="251.95" y="146.67" width="92.27" height="74.14" rx="15.43"/></g>
            <g id="maincolor" :style="{fill:caseColor,stroke:strokecolor}"><rect class="cls-2" x="265.27" y="141.86" width="65.64" height="83.76" rx="11.18" transform="translate(481.83 -114.34) rotate(90)"/></g>
            <g id="darkzone" class="darkzone"><path d="M335.27,153c-2.89-1.37-.77-2.07-6.94-2.07h-61.4c-5.23.26-4.87,1.38-6.19,2.07Z"/><path d="M258.69,218.73c2.89,1.38,3,2.08,9.15,2.08h61.4c5.23-.26,6.91-1.39,8.24-2.08Z"/></g>
        </svg>
    </svg>
    <p v-if="showcase == 10" :style="{color:numbercolor,left:numleft,top:numtop}" >{{customnum}}</p>
    </div>



</div>
</template>


<script>
import {bus} from '../main';
export default {
    name:"sidecase",
    data(){
        return{
            strokecolor:'rgb(100, 100, 100)',
            customnum:'',
            numbercolor:'black',
            nummoveleft:23.2,
            nummovetop:37

        }
    },
    computed:{
        numleft:function(){
            return (this.nummoveleft+this.caseX*0.13)+'%'
        },
        numtop:function(){
            return (this.nummovetop+this.caseY*0.25)+'%'
        }
        
    },

    props:
        ['caseColor','caseX','caseY','showcase'],

    mounted(){
        bus.$on('caseinfo',(number)=>{
            this.customnum = number;
        })
        bus.$on('numcolor',(color)=>{
            this.numbercolor = color;
        })
    }
    
    
}
</script>

<style >
    #casediv{
        z-index: 6;
    }

    .darkzone3 {
        fill: black;
        opacity: 0.3;
        z-index: 10;
        
    }

    .numberdiv {
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .numberdiv p {
        color: black;
        width: 30%;
        font-size: 60px;
        font-weight: 500;
        text-align: center;
        line-height: 60px; 
        font-family: 'Lobster', cursive;
        position: absolute;
        overflow: hidden;
        position: absolute;
        /* left: 23.5%;
        top: 37%; */
    }

    @media (max-width:1200px) {
        .numberdiv p {
            font-size: 50px;
            top: 36%;
            line-height: 50px;
        }
    }
</style>