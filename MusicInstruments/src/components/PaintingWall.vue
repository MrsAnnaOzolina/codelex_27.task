<script setup lang="ts">
import { onMounted, ref, watch } from 'vue';
import Slider from './Slider.vue';

const audioGuitar = new Audio('../../public/audio/Guitar.wav')
const  audioViolin = new Audio('../../public/audio/violin.wav')
const  audioPiano = new Audio('../../public/audio/piano.wav')
const  audioTriangle = new Audio('../../public/audio/triangle.mp3')
const  audioTrumpet = new Audio('../../public/audio/trumpet.wav')
const  audioSaxophone = new Audio('../../public/audio/SAXY4.wav')
const  audioTrumpet2 = new Audio('../../public/audio/FLUTE3.wav')
const value = 1
const volumeSVG = ref(false)


const  playSound = (value:number) => {
  if (value === 1 ){
    audioGuitar.play()
  }
  if (value === 2) {
    audioViolin.play()
  }
  if( value === 3 ){
    audioPiano.play()
  }
  if( value === 4 ){
    audioTrumpet.play()
  }
  if( value === 5 ){
    audioTriangle.play()
  }
  if( value === 6 ){
    audioSaxophone.play()
  }
  if( value === 7 ){
    audioTrumpet2.play()
  }
  if( value === 8 ){
    audioTrumpet2.play()
  }
}

const changeVolume = (volumeValue:number) => { 
  console.log(volumeValue)
  // if (volumeValue === 0){
  //   volumeSVG.value = true
  // }
  audioGuitar.volume = volumeValue;
  audioPiano.volume=volumeValue;
  audioTriangle.volume=volumeValue;
  audioTrumpet.volume=volumeValue;
  audioViolin.volume=volumeValue
}



</script>

<template>
  <!-- <Slider :value="0.75" :max="1"/> -->
<h1 class="title">My musical wall</h1>
  <div class="wall">
<div class="wall__image wall__first">
    <img  @click="playSound(2)" class="wall--image" src="../../public/Violin.jpg" alt="" width="200">
   </div>
  
   <div class="wall__image wall__second">
    <img @click="playSound(1)" class="wall--image" src="../../public/Guitar.jpg" alt="" width="100">
  </div>
  <div class="wall__image wall__third">
  <img  @click="playSound(5)" class="wall--image" src="../../public/traingle.jpeg" alt="" height="120">
</div>
<div class="wall__image">
    <img  @click="playSound(6)"  class="wall--image" src="../../public/saxophone.jpeg" alt="" width="100">
  </div>
  <div class="wall__image wall__fifth">
    <img  @click="playSound(4)"  class="wall--image" src="../../public/trumpet2.jpeg" alt="" width="150">
  </div>
  <div>
    <img  @click="playSound(3)"  class="wall--image" src="../../public/Piano.jpg" alt="" width="100">
  </div>
<div class="wall__image">
  <img  @click="playSound(7)" class="wall--image" src="../../public/trumpet.jpeg" alt="" width="100">
</div>
<div class="wall__image">
  <img  @click="playSound(8)" class="wall--image" src="../../public/drums.jpeg" alt="" width="200">
</div>

  </div>

  <div class="footer"> 
  <div></div>

<img src="../../public/sofa.svg" alt="" width="350">
  <div class="volumeSlider">
    <!-- <span v-if="volumeSVG"> 1</span>
    <span v-if="!volumeSVG">2</span> -->
    <!-- <svg width="16" height="22" viewBox="0 0 16 22" fill="none" xmlns="http://www.w3.org/2000/svg">
<path d="M13.6667 1.66669L7.00002 7.00002H1.66669V15H7.00002L13.6667 20.3334V1.66669Z" stroke="white" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"/>
</svg> -->

<span class="volumeImage">
   <svg  width="30" height="22" viewBox="0 0 30 22" fill="none" xmlns="http://www.w3.org/2000/svg">
<path d="M13.6667 1.66669L7.00002 7.00002H1.66669V15H7.00002L13.6667 20.3334V1.66669Z" stroke="white" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M24.4266 1.5733C26.9262 4.07367 28.3305 7.46445 28.3305 11C28.3305 14.5355 26.9262 17.9263 24.4266 20.4266M19.72 6.27997C20.9698 7.53016 21.6719 9.22554 21.6719 10.9933C21.6719 12.7611 20.9698 14.4565 19.72 15.7066" stroke="white" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"/>
</svg>
</span>

  <input  type="range" min="0" max="1" step="0.1" v-model="value" @change="changeVolume(value)">
</div>

</div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Beth+Ellen&family=Shadows+Into+Light&display=swap');
.title{
  display: flex;
  justify-content: center;
  margin-bottom: 30px;
  margin-top: 0;
  font-family: 'Beth Ellen', cursive;
font-family: 'Shadows Into Light', cursive;
font-size: 60px;
color: rgb(61, 57, 57);


}
.volumeImage{
  margin-right: 10px;
}
.volumeSlider{
  margin: 20px;
 margin-bottom: 50px;
}
.wall{
  display: grid;
  grid-template-columns: repeat(5, 200px);  
  justify-content: center;
  gap: 20px;
}
.wall__third{
  grid-column: 2;
  grid-row: 2;
  justify-self: flex-end;
}
.wall__first{
  grid-column: 1;
  grid-row: 1/3;
}
.wall__fifth{
  grid-column: 4;
  grid-row: 1/3;
  align-self: center;
}
.wall--image{
  border-radius: 5px;
  box-shadow: 10px 10px 5px rgb(106, 112, 115);
  /* zoom:75%; */
}
.wall--image:hover{
  color: white;
  box-shadow: 0 5px 15px #afe0f5;
}
.footer{
  display: grid;
  grid-template-columns: repeat(3, 40vw);  
  align-items: flex-end;
  justify-content: center;
}
</style>
