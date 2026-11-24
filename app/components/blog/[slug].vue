<template>
  <div class="post-page" v-if="post">
    <div class="post-hero" :style="{ backgroundImage: `url(${post.image})` }">
      <div class="hero-overlay">
        <span class="date">{{ post.date }}</span>
        <h1>{{ post.title }}</h1>
      </div>
    </div>

    <div class="post-content">
      <div class="post-body" v-html="post.content"></div>
    </div>
  </div>
</template>

<script setup>
import { useRoute } from 'vue-router'
import { computed } from 'vue'

const route = useRoute()

const posts = [
  {
    slug: 'fotograficzna-podroz',
    title: 'Fotograficzna podróż',
    date: '19.06.2019',
    image: 'https://images.pexels.com/photos/1578750/pexels-photo-1578750.jpeg?auto=compress&cs=tinysrgb&w=1600',
    content: `<p>Witajcie, poszukiwacze piękna i chwil! Jestem Grace i z radością dzielę się z Wami moim fotograficznym światem...</p><p>W tym wpisie na blogu dołączcie do mnie w podróż pełną odkryć...</p>`
  },
  {
    slug: 'soczewka-na-swiat',
    title: 'Soczewka na świat',
    date: '19.06.2019',
    image: 'https://images.pexels.com/photos/167699/pexels-photo-167699.jpeg?auto=compress&cs=tinysrgb&w=1600',
    content: `<p>Hej, drodzy podróżnicy i entuzjaści fotografii! Z tej strony Grace...</p>`
  }
  // dodaj resztę
]

const post = computed(() => posts.find(p => p.slug === route.params.slug))
</script>

<style scoped>
.post-page {
  background: #1d382e;
  min-height: 100vh;
}

.post-hero {
  height: 70vh;
  background-size: cover;
  background-position: center;
  position: relative;
  display: flex;
  align-items: flex-end;
}

.hero-overlay {
  width: 100%;
  padding: 60px 50px 80px;
  background: linear-gradient(transparent, #1d382e);
}

.date {
  font-size: 0.8rem;
  letter-spacing: 1px;
  color: #8aab9a;
}

h1 {
  font-size: 3.8rem;
  color: #f0f5f2;
  margin: 10px 0 0;
  font-weight: 500;
  max-width: 800px;
}

.post-content {
  padding: 40px 50px 100px;
  max-width: 760px;
}

.post-body {
  color: #d0ddd4;
  font-size: 1.05rem;
  line-height: 1.75;
}

.post-body p {
  margin-bottom: 20px;
}

@media (max-width: 768px) {
  h1 { font-size: 2.4rem; }
  .post-hero { height: 50vh; }
  .hero-overlay, .post-content { padding-left: 20px; padding-right: 20px; }
}
</style>