<template >
<div id="casediv"> 
    <p  v-if="showcase !== 8" id="number" :style="{left:caseX*1.3+140+'px',top:caseY*1.3+82+'px',color:testcolor}" >{{customnum}}</p>
    <svg v-show="showcase == 8" id="case" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 283.46 170.08">
        <svg :x="caseX" :y="caseY">
            <g id="case1" :style="{fill:caseColor}"><path d="M132.48,100.76c-6.91-6.75-13.86-13.47-20.73-20.28-1.91-1.89-3.74-4.18-2.17-7,1.46-2.6,3.42-4.63,7-4.6,17.79.18,35.58.17,53.36.22a1.91,1.91,0,0,1,1.63.88,23.14,23.14,0,0,1,2.35,6,17.2,17.2,0,0,1,.31,7.21,74.48,74.48,0,0,1-1.76,8.24c-2,6.38-4,10.12-12.6,9.72C150.76,100.73,141.61,100.84,132.48,100.76ZM168.91,71"/></g>
            <g id="caselight1" class="lightzone"><path d="M170.3,72.23l-55.43.53c.86-2.32,2.47-2.11,4-2.11h49.29C168.77,70.68,170.3,70.42,170.3,72.23Z"/></g>
            <g id="casedark1" class="darkzone"><path d="M169.3,94.41c-1,3.19-3.69,5.12-7.74,5.15-7.8,0-15.6,0-23.4,0-3.66,0-6-2.21-8.94-4.16C143.74,95.79,151,97.66,169.3,94.41Z"/><path d="M174.23,83.11a74.48,74.48,0,0,1-1.76,8.24c-2,6.38-4,10.12-12.6,9.72-9.11-.44-18.26-.33-27.39-.41-6.91-6.75-13.86-13.47-20.73-20.28a8.85,8.85,0,0,1-2.65-4c-.51,2.25,1,4.13,2.65,5.73,6.87,6.81,13.82,13.53,20.73,20.28,9.13.08,18.28,0,27.39.41,8.6.4,10.6-3.34,12.6-9.72a74.48,74.48,0,0,0,1.76-8.24,17,17,0,0,0,.21-3.77A17.12,17.12,0,0,1,174.23,83.11Z"/></g>
        </svg> 
    </svg>  

    
    <svg v-show="showcase == 9" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 283.46 170.08">
        <svg :x="caseX" :y="caseY" >
            <g id="case2" style="fill:#fff;stroke:#666;stroke-width:0.25px;"><ellipse  cx="141.73" cy="85.03" rx="44.86" ry="36"/></g>
            <g id="casedark2">
            <ellipse :style="{fill:caseColor,stroke:strokecolor}" cx="141.73" cy="85.03" rx="41.75" ry="33.5"/>
            <path class="moredark" d="M186.6,85.05c0,19.88-20.09,36-44.87,36s-44.86-16.12-44.86-36c0,0,3.06,34.39,44.86,34.39S186.6,85.05,186.6,85.05Z"/>
            <path class="moredark" d="M107.8,66.05c11-13.3,29.33-14.52,33.93-14.52,9.76,0,27.5,4.54,34,14.61,0,0-11-13.58-34-13.58A50.87,50.87,0,0,0,107.8,66.05Z"/></g>
        </svg>
    </svg>

    
    <svg v-show="showcase == 10" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 283.46 170.08">
        <svg :x="caseX" :y="caseY">
            <g id="case3" style="fill:#fff;stroke:#666;stroke-width:0.25px;"><rect class="cls-1" x="95.6" y="47.97" width="92.27" height="74.14" rx="15.43"/></g>
            <g id="caseline3" :style="{fill:caseColor,stroke:strokecolor}"><rect class="cls-2" x="108.91" y="43.16" width="65.64" height="83.76" rx="11.18" transform="translate(226.77 -56.69) rotate(90)"/></g>
            <g id="casedark3"><path class="moredark" d="M178.92,54.3c-2.89-1.38-.78-2.08-6.94-2.08H110.57c-5.22.26-4.86,1.39-6.19,2.08Z"/><path class="moredark" d="M102.34,120c2.89,1.38,3,2.08,9.14,2.08h61.41c5.22-.26,6.91-1.39,8.23-2.08Z"/></g>
        </svg>
    </svg>
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
            testcolor:'black',
        }
    },
    methods:{
        
    },

    props:
        ['caseColor','caseX','caseY','showcase'],

    mounted(){
        bus.$on('caseinfo',(number)=>{
            this.customnum = number;
        })
        bus.$on('numcolor',(color)=>{
            this.testcolor = color;
        })
    }
    
    
}
</script>

<style >
    #casediv{
        width: 370px;
        height: auto;
        position: absolute;
        left: 475px;
        top: 240px;
        z-index: 13;
    }

    .moredark {
        fill: black;
        opacity: 30%;
        z-index: 10;
        
    }

    #number {
        position: absolute;
        color: black;
        font-size: 60px;
        text-align: center;
        width: 90px;
        line-height: 60px;
        font-family: 'Lobster', cursive;
        font-weight: 500;
        overflow: hidden;
    }
</style>