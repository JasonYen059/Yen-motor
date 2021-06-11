<template >
<div id="lightdiv">
    <svg  v-show="showlight == 19" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 170.08 170.08">
        <svg :x="lightX" :y="lightY">
            <g id="lightyellow" style="fill:#fcfc44;"><path d="M93.11,64.91s13.84,13.89,2,36.14Z"/></g>
            <g id="light2" :style="{fill:lightColor}"><path d="M89.6,102.77c.48,2.28,5.37,2.79,5.94-4s-.68-22.6-.68-22.6-.62-12.47-3.44-14.06-4.06,1.38-4.06,1.38h0s-18.63,4.9-19.54,19.32,16,19.31,21.77,19.93"/></g>
            <g id="lightdark" class="darkzone"><path d="M94.87,101.76c5.9-11.65,5-18.77,5-18.77L67.8,84.21c.4,11.69,12.28,16.84,21.8,18.56C89.6,102.77,92.21,107,94.87,101.76Z"/><path d="M87.64,65.91s-1-3.34.31-1.85,1.74,13.37,1.74,13.37.58,14.85.32,21.18-1.1,3.64-1.32,1.52C88.49,98.25,90.25,84,87.64,65.91Z"/><path d="M93.31,65.85s-.67-1.83.18-.39,2,12.42,2,12.42,1.13,14.43.2,20.49c-.64,4.19-.7,3.52-.85,1.46C94.66,98,95.59,82.89,93.31,65.85Z"/></g>
        </svg>
    </svg>

    <svg v-show="showlight == 20" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 170.08 170.08">   
        <svg :x="lightX" :y="lightY">
            <g id="lightyellow" style="fill:#fcfc44;"><path d="M94.12,68.31s12.11,10.76,1.77,28Z"/></g>
            <g id="light2" :style="{fill:lightColor}"><path d="M91.05,97.64c.42,1.76,4.7,2.16,5.2-3.08s-.6-17.5-.6-17.5-.54-9.66-3-10.89a2.5,2.5,0,0,0-3.55,1.07h0S72.8,71,72,82.2s14,15,19,15.44"/></g>
            <g id="lightdark" class="darkzone"><path d="M95.66,96.86c5.16-9,4.4-14.54,4.4-14.54L72,83.27c.35,9,10.74,13,19.07,14.37C91.05,97.64,93.34,100.92,95.66,96.86Z"/><path d="M89.34,69.09s-.89-2.59.27-1.43S91.13,78,91.13,78s.51,11.5.28,16.41-1,2.82-1.16,1.17C90.08,94.13,91.62,83.11,89.34,69.09Z"/><path d="M94.29,69.05s-.58-1.42.17-.31,1.7,9.62,1.7,9.62,1,11.18.18,15.87c-.56,3.24-.62,2.72-.74,1.13C95.48,94,96.29,82.24,94.29,69.05Z"/></g>
        </svg>
    </svg>

</div>
</template>


<script>
export default {
    name:"light",
    data(){
        return{
            
        }
    },

    props:
        ['lightColor','lightX','lightY','showlight']
    
}
</script>

<style >
    #lightdiv{
        width: 220px;
        height: auto;
        position: absolute;
        top: 160px;
        z-index: 0;
        left: 863px;
    }
    .lightzone05{
        fill: white;
        opacity: 50%;
    }
    .darkzone02{
        fill: black;
        opacity: 20%;
    }   
    

   
</style>