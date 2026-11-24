<template>
  <section class="carousel-section">
    <div class="carousel-wrapper">
      <div class="carousel-track" :style="{ transform: `translateX(-${offset}px)` }">
        <div v-for="(img, i) in displayImages" :key="i" class="carousel-slide">
          <img :src="img.src" :alt="img.alt" />
        </div>
      </div>

      <button class="nav prev" @click="prev">‹</button>
      <button class="nav next" @click="next">›</button>
    </div>
  </section>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'

const images = [
  { src: 'https://images.pexels.com/photos/167699/pexels-photo-167699.jpeg?auto=compress&cs=tinysrgb&w=800&fit=crop', alt: 'Lake forest' },
  { src: 'https://images.pexels.com/photos/3408744/pexels-photo-3408744.jpeg?auto=compress&cs=tinysrgb&w=800&fit=crop', alt: 'Woman forest' },
  { src: 'https://images.pexels.com/photos/1133957/pexels-photo-1133957.jpeg?auto=compress&cs=tinysrgb&w=800&fit=crop', alt: 'Misty lake' },
  { src: 'https://images.pexels.com/photos/1366630/pexels-photo-1366630.jpeg?auto=compress&cs=tinysrgb&w=800&fit=crop', alt: 'Woman nature' },
  { src: 'https://images.pexels.com/photos/1028225/pexels-photo-1028225.jpeg?auto=compress&cs=tinysrgb&w=800&fit=crop', alt: 'Forest path' },
  { src: 'https://images.pexels.com/photos/1578750/pexels-photo-1578750.jpeg?auto=compress&cs=tinysrgb&w=800&fit=crop', alt: 'Misty trees' },
  { src: 'https://images.pexels.com/photos/1446624/pexels-photo-1446624.jpeg?auto=compress&cs=tinysrgb&w=800&fit=crop', alt: 'Hands cup' },
  { src: 'https://images.pexels.com/photos/1671325/pexels-photo-1671325.jpeg?auto=compress&cs=tinysrgb&w=800&fit=crop', alt: 'Squirrel' },
  { src: 'https://images.pexels.com/photos/1578751/pexels-photo-1578751.jpeg?auto=compress&cs=tinysrgb&w=800&fit=crop', alt: 'Forest table' },
  { src: 'https://images.pexels.com/photos/1446625/pexels-photo-1446625.jpeg?auto=compress&cs=tinysrgb&w=800&fit=crop', alt: 'Cup nature' }
]

const displayImages = computed(() => {
  const arr = []
  for (let i = 0; i < 10; i++) arr.push(...images)
  return arr
})

const offset = ref(0)
const slideWidth = 268
let interval = null

function next() {
  offset.value += slideWidth
}

function prev() {
  offset.value -= slideWidth
}

onMounted(() => {
  interval = setInterval(next, 3500)
})

onUnmounted(() => {
  clearInterval(interval)
})
</script>

<style scoped>
.carousel-section {
  background: #1a3a2a;
  padding: 0;
  position: relative;
  width: 100%;
}

.carousel-wrapper {
  position: relative;
  overflow: hidden;
  height: 380px;
}

.carousel-track {
  display: flex;
  height: 100%;
  transition: transform 0.6s ease;
  gap: 8px;
}

.carousel-slide {
  min-width: 260px;
  height: 100%;
  flex-shrink: 0;
}

.carousel-slide img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  filter: grayscale(100%);
}

.nav {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(255, 255, 255, 0.92);
  border: none;
  width: 34px;
  height: 34px;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1.3rem;
  color: #1a3a2a;
  z-index: 3;
}

.nav.prev { left: 10px; }
.nav.next { right: 10px; }

.nav:hover {
  background: white;
}

@media (max-width: 768px) {
  .carousel-wrapper {
    height: 260px;
  }
  .carousel-slide {
    min-width: 200px;
  }
}
</style>