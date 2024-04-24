<script setup>
import { ref } from 'vue'
const count = ref(0);
const showAnswer = ref(false);
const showFunFact = ref(false);

const today = new Date();
const dateModal = ref("");

const date = ref({
  year: today.getFullYear().toString(2),
  month: (today.getMonth() + 1).toString(2),
  day: today.getDate().toString(2),
});

function dateCallback() {
  const dateArr = ["3", "3", "2"]
  
  date.value.year = dateArr[0].toString(2);
  date.value.month = dateArr[1].toString(2);
  date.value.day = dateArr[2].toString(2);
}
</script>

<template>
  <body>
    <div class="carousel-wrapper">
      <div class="carousel">
        <button class="slide-move" @click="count = (count + 3) % 4">&lt;</button>
        <div class="slide">

          <div class="slide0" v-if="count === 0">
            <h1>Why are ducks important to the economy?</h1>
          </div>
  
          <div class="slide1" v-else-if="count === 1">
            <div class="slide1-top">
              <p>Input a date:</p>
              <input type="date" v-model="dateModal" @input="dateCallback">
            </div>
            <p>{{ date.day }} - {{ date.month }} - {{ date.year }}</p>
          </div>
  
          <div class="slide2" v-else-if="count === 2">
            <h1>
              <bold><i>Lorem Ipsum</i>is simply dummy text of the printing and typesetting industry.</bold>
            </h1>
            <h2>Lorem Ipsum has been the industry's standard dummy text</h2>
            <p>It has survived not only five centuries, but also the leap into electronic typesetting, remaining
              essentially
              unchanged. It was popularized in the 1960s with the release of Letraset sheets containing Lorem Ipsum
              passages, and more recently with desktop publishing software like Aldus PageMaker including versions of
              Lorem
              Ipsum.</p>
          </div>
  
          <div class="slide3" v-else-if="count === 3">
            <img src="@/assets/challenge.png" alt="WebDev">
          </div>

        </div>
        <button class="slide-move" @click="count = (count + 1) % 4">&gt;</button>
      </div>

      <div class="carousel-pagination">
        <button @click="count = 0"></button>
        <button @click="count = 1"></button>
        <button @click="count = 2"></button>
        <button @click="count = 3"></button>
      </div>

      <div class="under-text">
        <template v-if="count === 0">
          <button @click="showAnswer = true" v-if="!showAnswer">show answer</button>
          <p v-if="showAnswer">Ducks are very cute therefore make people happy, and it's scientifically proven that
            happy people are more productive in the workplace.</p>
        </template>
        <template v-else-if="count === 1">
          <p>22/04/2001</p>
          <button @click="showFunFact = true" v-if="!showFunFact">fun fact</button>
          <p v-if="showFunFact">Happy Birthday to Shrek 1 Movie!</p>
        </template>
      </div>
    </div>


  </body>
</template>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

h1,
h2,
p {
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
}

body {
  height: 100svh;
  width: 100svw;
  color: black;
  display: flex;
  justify-content: center;
  align-items: center;
}

.carousel-wrapper {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.carousel {
  display: flex;
  align-items: center;
  margin: 0 2rem;
  gap: 15px;
}

.slide-move {
  width: 35px;
  height: 35px;
  border-radius: 50%;
  border: none;
  background-color: #b9deee;
  color: #003c56;
  font-weight: 700;
  cursor: pointer;
}

.slide-move:hover {
  scale: 1.1;
}

.slide {
  max-width: 750px;
  width: 100vw;
  height: 500px;
  background-color: white;
  border-radius: 40px;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}

.slide1 {
  font-size: 2rem;
}

.slide1-top {
  display: flex;
  gap: 1ch;
  margin-bottom: 0.5rem;
}

.slide2 {
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 2rem;
}

.slide3>img {
  object-fit: cover;
  width: 100%;
  height: 100%;
}

.carousel-pagination {
  margin: 1rem 0;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 10px;
}

.carousel-pagination>button {
  background-color: #008ECC;
  border: none;
  opacity: 30%;
  width: 10px;
  height: 10px;
  border-radius: 50%;
  cursor: pointer;
}

.under-text {
  margin: 0 auto;
  position: absolute;
  text-align: center;
  color: #b9deee4d;
  font-size: 1.3rem;
  top: 100%;
}

:is(.slide, .under-text)>div {
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