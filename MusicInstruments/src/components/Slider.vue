<script setup lang="ts">

import { ref, onMounted, computed, reactive } from 'vue'
import throttle from 'lodash/throttle'
import { propsToAttrMap } from '@vue/shared';

const props = defineProps<{
  value: number
  max: number
}>()
const bar = ref()
const handler = ref()
let handlerWidth = ref(0) 
let barWidth = ref(0)


let onWindowsResize = () => { 
    calcDimensions();
    
}

const calcDimensions = () => { 
    // console.log(bar.value, handler.value)
    handlerWidth.value = handler.value.offsetWidth
    barWidth.value = bar.value.offsetWidth
    // console.log(barWidth)
    
 }

 const delta = computed(()=> props.value/props.max )
 const fillStyle = computed(()=>{
    return {
        transformOrigin:"left center",
        transform: `scaleX(${delta.value})`
    }
 })
 const handleStyle = computed(()=> {
    
    // console.log(barWidth)
    // handlerWidth = handler.value.offsetWidth
    // barWidth = bar.value.offsetWidth
    console.log(barWidth.value)
    return {

         transform:`translateX(${barWidth.value * delta.value- (handlerWidth.value*0.5)}px)`
    }
 })
onMounted(()=>{
    onWindowsResize = throttle(onWindowsResize, 2000 )
    calcDimensions(); 
    window.addEventListener('resize', onWindowsResize)
    // console.log(barWidth.value, delta.value)
})



</script>

<template>
    <div class="volume">
        <p>Volume</p>
    <div class="slider">
        <div class="slider__bar"  ref="bar">
            <div class="slider__handler"  :style="handleStyle" ref="handler"></div>
                <div class="slider__fill" :style="fillStyle">
                  
                </div>
               
        
        </div>
    </div>
</div>
</template>

<style> 
.volume{
    width: 30vw;
    margin:20px;
}
.slider{
    cursor: pointer;
    width: 100%;
    display: flex;
    align-items: center;
    height: 24px;
}
.slider__bar{
    position: relative;
    width: 100%;
    height: 5px;
    background-color: lightgray;
    border-radius: 5px;
}
.slider__handler{
    width: 16px;
    height: 16px;
    border-radius: 50%;
    background-color: rgb(59, 54, 54);
    position: absolute;
    left: 0;
    top: calc(50% - 8px);
    z-index:1;
}
.slider__fill{
    /* position: relative; */
    position: absolute;
    height: 100%;
    width: 100%;
    background-color: red;
z-index: 0;
}

</style>