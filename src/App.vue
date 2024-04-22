<script setup>
import { ref } from 'vue'
let count = ref(0);
let message = "Happy Birthday to Shrek 1 Movie!";
let showMessage = ref(false);
let answer = "Ducks are very cute therefore make people happy, and it's scientifically proven that happy people are more productive in the workplace."
let showAnswer = ref(false)
</script>

<template>

  <slides>
    <button class="MoveBtn" @click="count = (count + 3)%4"><</button>

    <slideContainer :class="{ 'slide3Background': count === 3 }">
        <div class="fadeIn" style="font-size: 250%; font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif; " v-if="count===0">Why are ducks important to the economy?</div>
        <div class="fadeIn" style="font-size: 250%; font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif; " v-else-if="count===1">10110-100-11111010001</div>
        <div class="fadeIn" v-else-if="count===2">
          <slide2Content>
            <p style="font-size: 200%; font-weight: bold;"><span style="font-style: italic; font-weight: bold;">Lorem Ipsum</span> is simply dummy text of the printing and typesetting industry.</p>
            <p style="font-size: 150%;"><span style="font-style: italic;">Lorem Ipsum</span> has been the industry's standard dummy text </p>
            <p style="font-size: 100%;">It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.</p>
          </slide2Content>
        </div>
        <div class="fadeIn" v-else-if="count===3"></div>
    </slideContainer>

    <button class="MoveBtn" @click="count = (count + 1)%4">></button>
  </slides>
  
  <br>
  <btnContainer>
    <button class="SlideBtn" @click="count = 0"></button>
    <button class="SlideBtn" @click="count = 1"></button>
    <button class="SlideBtn" @click="count = 2"></button>
    <button class="SlideBtn" @click="count = 3"></button>
  </btnContainer>
  <br>

  <paragraph>
      <p1 class="fadeIn" v-if="count===0">
        <button v-if="!showAnswer" @click="showAnswer=true">show answer</button>
        <msg v-if="showAnswer" style="font-size: 17px; font-weight: lighter; font-family:Arial, Helvetica, sans-serif; opacity: 30%;">{{ answer }}</msg>
      </p1>
      <p2 class="fadeIn" v-else-if="count===1"> 
        <p>22/04/2001</p> 
        <button v-if="!showMessage" @click="showMessage=true">fun fact</button>
        <msg v-if="showMessage" style="font-size: 17px; font-weight: lighter; font-family:Arial, Helvetica, sans-serif; opacity: 30%;">{{ message }}</msg>
      </p2>
  </paragraph>
</template>

<style>
  slides {
    margin-top: 10vh;
    display: flex;
    gap: 30px;
    flex-direction: row;
    justify-content: center;
    align-items: center;
  }
  slideContainer {
    background-color: white;
    width: 750px; 
    height: 500px;
    position: relative;
    border-radius: 5%;
    display: flex;
    justify-content: center;
    align-items: center;
    /*transition: opacity 0.5s ease;*/
  }
  btnContainer {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    gap: 10px;
  }
  .SlideBtn {
    background-color: #008ECC;
    border: none;
    opacity: 30%;
    width: 10px;
    height: 10px;
    border-radius: 50%;
  }
  .MoveBtn {
    height: 35px;
    width: 35px;
    border-radius: 70%;
    border: none;
    background-color: #b9deee;
    color:#003c56;
    font-weight: bolder;
    font-size: larger;
  }
  div {
    color:black;
  }
  paragraph {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    align-content: center;
    text-align: center;
    color:#b9deee;
    font-size: 150%;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  }
  slide2Content {
    display: flex;
    flex-direction: column;
    gap: 20px;
    margin-left: 50px;
    margin-right:  50px;
  }
  .slide3Background {
      background-image: url('assets/challenge.png');
      background-size: cover;
      background-position: center;
    }
  .fadeIn {
	opacity: 1;
	animation-name: fadeInOpacity;
	animation-iteration-count: 1;
	animation-timing-function: ease-in;
	animation-duration: 0.6s;
  }

@keyframes fadeInOpacity {
	0% {
		opacity: 0;
	}
	100% {
		opacity: 1;
	}
}

</style>