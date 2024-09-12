<script setup>
import { ref } from 'vue'

// Click Counter
const count = ref(0)
const increment = () => {
  count.value++
}

// Box Color Changer
const colors = ['#FF6B6B', '#4ECDC4', '#FFD93D', '#1A535C', '#FF3F34']
const boxColor = ref(colors[0])
const changeColor = () => {
  const randomIndex = Math.floor(Math.random() * colors.length)
  boxColor.value = colors[randomIndex]
}

// Image Carousel
const images = [
  'https://superlive.id/storage/articles/5d9e2a66-9778-4bee-adc5-b93558992f70.jpg',
  'https://indonesia-az.com/wp-content/uploads/2023/07/Merbabu-via-Suwanting-Indonesia-A-Z.jpeg',
  'https://asset.kompas.com/crops/OD9itl1d8QHvxgLLaKN3u13KhYw=/1x0:1000x666/750x500/data/photo/2023/02/28/63fdb9789cf09.jpg',
  'https://cdn1-production-images-kly.akamaized.net/NClgcQyjpiJ84m3IpbUYly7wn4k=/1200x900/smart/filters:quality(75):strip_icc():format(webp)/kly-media-production/medias/4556165/original/055409600_1693311908-000_HKG2004041760543.jpg'
]
const currentImageIndex = ref(0)

const nextImage = () => {
  currentImageIndex.value = (currentImageIndex.value + 1) % images.length
}

const prevImage = () => {
  currentImageIndex.value = (currentImageIndex.value - 1 + images.length) % images.length
}
</script>

<template>
  <div class="container">
    <!-- Click Counter -->
    <div class="counter-section">
      <h1>Click Counter</h1>
      <p class="count">{{ count }}</p>
      <button class="btn" @click="increment">Tambah</button>
    </div>

    <!-- Box Color Changer -->
    <div class="color-section">
      <h1>Box Color Changer</h1>
      <div :style="{ backgroundColor: boxColor }" class="color-box"></div>
      <button class="btn" @click="changeColor">Ganti Warna</button>
    </div>

    <!-- Image Carousel -->
    <div class="carousel-section">
      <h1>Image Carousel</h1>
      <div class="carousel">
        <button class="carousel-btn" @click="prevImage">❮</button>
        <img :src="images[currentImageIndex]" class="carousel-image" />
        <button class="carousel-btn" @click="nextImage">❯</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* General Container */
.container {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
  gap: 30px;
  padding: 20px;
  background-color: #f9f9f9;
}

/* Counter Section */
.counter-section {
  text-align: center;
  background-color: #fff;
  padding: 20px;
  border-radius: 12px;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
}

.count {
  font-size: 3rem;
  font-weight: bold;
  margin-bottom: 10px;
  color: #007bff;
}

/* Color Section */
.color-section {
  text-align: center;
  background-color: #fff;
  padding: 20px;
  border-radius: 12px;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
}

.color-box {
  width: 150px;
  height: 150px;
  margin: 20px auto;
  border-radius: 10px;
  transition: background-color 0.3s ease;
}

/* Carousel Section */
.carousel-section {
  text-align: center;
  background-color: #fff;
  padding: 20px;
  border-radius: 12px;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
}

.carousel {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
}

.carousel-image {
  width: 300px;
  height: 200px;
  object-fit: cover;
  border-radius: 10px;
}

.carousel-btn {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 10px;
  border-radius: 50%;
  cursor: pointer;
  font-size: 1.5rem;
  transition: background-color 0.3s ease;
}

.carousel-btn:hover {
  background-color: #0056b3;
}

/* Button Styles */
.btn {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 10px 20px;
  font-size: 1rem;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.btn:hover {
  background-color: #0056b3;
}

/* Responsive Design */
@media (max-width: 768px) {
  .container {
    flex-direction: column;
    align-items: center;
  }

  .carousel-image {
    width: 250px;
    height: 150px;
  }
}
</style>
