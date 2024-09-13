<template>
  <div id="app">
    <!-- Title -->>
    <h1>Vue App Ifadah</h1>

    <!-- Sections Container -->
    <div class="section-container">

      <!-- Click Counter Section -->
<div class="card section click-counter-container">
  <h2 class="click-counter">Click Counter</h2>
  <div class="counter-display">
    <span>{{ clickCount }}</span>
  </div>
  <div class="counter-controls">
    <button @click="incrementCounter">+</button>
    <button @click="decrementCounter">-</button>
  </div>
  <button class="reset" @click="resetCounter">Reset</button>
</div>

      <!-- Box Color Changer Section -->
      <div class="card section color-box-container">
        <div class="color-box" :style="{ backgroundColor: currentColor }"></div>
        <button @click="changeColor">Change Box Color</button>

        <!-- Color Palette -->
        <div class="color-palette">
          <div
            v-for="color in colors"
            :key="color"
            :style="{ backgroundColor: color }"
            class="color-swatch"
            @click="currentColor = color"
          ></div>
        </div>
      </div>
    </div>

    <!-- Image Carousel Section -->
    <div class="card section carousel-container">
      <div class="carousel">
        <button class="arrow left-arrow" @click="prevImage">Left</button>
        <img :src="images[currentImage]" alt="Carousel Image" class="carousel-image" />
        <button class="arrow right-arrow" @click="nextImage">Right</button>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  data() {
    return {
      clickCount: 0,
      colors: ['#415d43', '#4f4f4f', '#9fac8a', '#7b5836', '#e1cbb1'],
      currentColor: '#415d43', 
      images: [
        'https://i.pinimg.com/originals/54/58/30/5458303d91ff080f07a7884b9f6ff2a7.gif',        
        'https://i.pinimg.com/originals/f3/e0/a5/f3e0a5eb29a20721639973c480793e8a.gif',
        'https://i.pinimg.com/originals/58/78/9f/58789f8e2d65c06f1218141cc8cd1db1.gif',
        'https://i.pinimg.com/originals/c6/29/d7/c629d70f467e722ef2b5a44b9fce08d4.gif'
      ],
      currentImage: 0
    };
  },
  methods: {
    incrementCounter() {
      this.clickCount++;
    },
    decrementCounter() {
      if (this.clickCount > 0) {
        this.clickCount--;
      }
    },
    resetCounter() {
      this.clickCount = 0;
    },
    changeColor() {
      this.currentColor = this.colors[Math.floor(Math.random() * this.colors.length)];
    },
    nextImage() {
      this.currentImage = (this.currentImage + 1) % this.images.length;
    },
    prevImage() {
      this.currentImage = (this.currentImage - 1 + this.images.length) % this.images.length;
    }
  }
};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap');

.click-counter-container {
  display: flex;
  flex-direction: column;
  align-items: center; 
}

/* Card Styling */
.card {
  background-color: #9a9a9a; 
  padding: 20px;
  border-radius: 50px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  width: 300px;
  transition: transform 0.3s, box-shadow 0.3s, background-color 0.3s; 
  margin: 10px auto;
}

/* Hover effect for cards */
.card:hover {
  transform: scale(1.05); /* zoom effect */
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); 
  background-color: #b0b0b0; 
}

button {
  background-color: #415d43; 
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 8px;
  cursor: pointer;
  font-size: 16px;
  transition: background-color 0.3s, transform 0.3s;
  margin: 5px 0; 
}

button:first-of-type {
  /* margin-top: 10px;  */
}

button:last-of-type {
  /* margin-bottom: 10px;  */
}


button.reset {
  margin-top: 10px; 
}

#app {
  background-color: #819171;
}

body {
  font-family: Poppins;
  background-color: #f0f8ff;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  margin: 0;
  color: #415d43; 
}

h1 {
  color: #ffffff; 
  font-size: 2.5rem;
  margin-bottom: 20px;
  text-align: center; 
  font-family: Poppins; 
}

.click-counter {
  font-family: 'Poppins';
  font-size: 20px; 
  font-weight: 700;
  color: #ffffff;
}

.section-container {
  display: flex;
  justify-content: center;
  gap: 20px;
  margin-bottom: 30px;
}

.section {
  text-align: center;
}

/* Container for the counter display and controls */
.counter-display {
  margin: 20px 0; 
  font-size: 24px; 
  font-weight: 700;
  color: #ffffff; 
  font-family: 'Poppins', sans-serif;
}

.counter-controls {
  display: flex;
  justify-content: center;
  gap: 10px; 
  align-items: center; 
}


button {
  background-color: #415d43; 
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 8px;
  cursor: pointer;
  font-size: 16px;
  transition: background-color 0.3s, transform 0.3s;
}

/* Button styles for hover and active states */
button:hover {
  background-color: #383838; 
  transform: scale(1.05); 
}

button:active {
  background-color: #383838; /* Darker gray on click */
}

/* Card Styling */
.card {
  background-color: #9a9a9a; 
  padding: 20px;
  border-radius: 50px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  width: 300px;
  transition: transform 0.3s, box-shadow 0.3s, background-color 0.3s; 
  margin: 10px auto;
}

/* Hover effect for cards */
.card:hover {
  transform: scale(1.05); /* Slight zoom effect */
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); 
  background-color: #b0b0b0; 
}
button.reset {
  margin-top: 10px; 
}

#app {
  background-color: #819171;
}

body {
  font-family: Poppins, sans-serif;
  background-color: #f0f8ff;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  margin: 0;
  color: #415d43; 
}

h1 {
  color: #ffffff; 
  font-size: 2.5rem;
  margin-bottom: 20px;
  text-align: center; 
  font-family: Poppins, sans-serif; 
}

.click-counter {
  font-family: 'Poppins', sans-serif;
  font-size: 20px; 
  font-weight: 700;
  color: #ffffff;
}

.section-container {
  display: flex;
  justify-content: center;
  gap: 20px;
  margin-bottom: 30px;
}

.section {
  text-align: center;
}

.color-box {
  width: 120px; 
  height: 120px; 
  margin: 20px auto;
  border-radius: 10px;
  transition: background-color 0.5s, transform 0.3s;
}

.color-box:hover {
  transform: rotate(10deg) scale(1.05); /* Rotate and zoom the box on hover */
}

.color-palette {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 10px;
  margin-top: 10px;
}

.color-swatch {
  width: 40px; 
  height: 40px; 
  border-radius: 50%;
  cursor: pointer;
  border: 2px solid #ffffff; 
}

.color-swatch:hover {
  border-color: #415d43; 
}

.carousel {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 30px; 
}

.carousel-image {
  width: 400px; 
  height: 250px; 
  border-radius: 10px;
  margin: 0 20px; 
  transition: opacity 0.5s, transform 0.3s;
}

.carousel-image:hover {
  transform: scale(1.05); /* Zoom effect on image hover */
}

.arrow {
  background-color: #415d43; 
  color: white;
  width: 90px; 
  height: 50px; 
  border-radius: 8px;
  cursor: pointer;
  font-size: 18px;
  border: none;
  text-align: center;
  transition: background-color 0.3s, transform 0.3s;
}

.arrow:hover {
  background-color: #383838; 
  transform: scale(1.1); /* Zoom effect on hover */
}

.arrow:active {
  background-color: #383838; /* Darker gray on click */
}

.left-arrow {
  margin-right: 10px;
}

.right-arrow {
  margin-left: 10px;
}

/* Card Styling */
.card {
  background-color: #9a9a9a; 
  padding: 20px;
  border-radius: 50px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  width: 25px; 
  transition: transform 0.3s;
  margin: 10px auto;
}

.card:hover {
  transform: scale(1.00); /* Slight zoom effect on hover */
}

.click-counter-container,
.color-box-container {
  flex: 1; 
  padding: 10px; 
  max-width: 300px;
}

.carousel-container {
  width: 90%; 
}
</style>


