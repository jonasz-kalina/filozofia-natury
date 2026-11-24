<template>
  <section class="post" v-if="post">
    <div class="post-hero" :style="{ backgroundImage: `url(${post.image})` }">
      <div class="post-hero-overlay"></div>
      <div class="post-hero-inner">
        <div class="post-hero-content">
          <div class="post-top">
            <span class="post-date">{{ post.date }}</span>
            <span class="post-tag">{{ post.categoryName }}</span>
          </div>
          <h1>{{ post.title }}</h1>
        </div>
      </div>
    </div>

    <div class="post-body">
      <div class="post-container">
        <div class="post-number">{{ String(post.index).padStart(2, '0') }}</div>

        <div class="post-content">
          <p v-for="(paragraph, i) in post.content" :key="i">{{ paragraph }}</p>
        </div>

        <div class="post-divider"></div>

        <NuxtLink to="/blog#posts" class="back-link">← Wróć do bloga</NuxtLink>
      </div>
    </div>
  </section>

  <section v-else class="not-found">
    <h1>Nie znaleziono</h1>
    <NuxtLink to="/blog">Wróć do bloga</NuxtLink>
  </section>
</template>

<script setup>
import { useRoute } from 'vue-router'
import posts from '~/data/posts.json'

const route = useRoute()

const post = computed(() => {
  return posts.find(p => p.slug === route.params.slug)
})
</script>

<style scoped>
.post-hero {
  height: 60vh;
  background-size: cover;
  background-position: center;
  position: relative;
  display: flex;
  align-items: flex-end;
}

.post-hero-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to bottom, rgba(0,0,0,0.15) 0%, rgba(15,28,24,0.9) 100%);
  z-index: 1;
}

.post-hero-inner {
  position: relative;
  z-index: 2;
  width: 100%;
  padding: 0 40px 50px;
  box-sizing: border-box;
}

.post-hero-content {
  max-width: 680px;
  margin: 0 auto;
}

.post-top {
  display: flex;
  align-items: center;
  gap: 14px;
  margin-bottom: 14px;
}

.post-date {
  font-size: 0.75rem;
  letter-spacing: 1px;
  color: #b8d0c4;
}

.post-tag {
  font-size: 0.7rem;
  letter-spacing: 0.5px;
  color: #fff;
  background: #e85a2a;
  padding: 5px 14px;
  border-radius: 20px;
  text-transform: uppercase;
  position: relative;
  z-index: 3;
}

.post-hero-content h1 {
  font-size: 3.6rem;
  font-weight: 500;
  color: #f0f5f2;
  margin: 0;
  line-height: 1;
}

.post-body {
  background: #0f1c18;
  padding: 70px 40px 100px;
}

.post-container {
  max-width: 680px;
  margin: 0 auto;
  position: relative;
}

.post-number {
  position: absolute;
  top: -10px;
  right: -160px;
  font-size: 7.5rem;
  font-weight: 200;
  color: #c8d5cc;
  opacity: 0.3;
  line-height: 0.8;
}

.post-content p {
  font-size: 1rem;
  color: #b8d0c4;
  line-height: 1.55;
  margin: 0 0 18px;
}

.post-divider {
  width: 60px;
  height: 2px;
  background: #e85a2a;
  margin: 40px auto 30px;
}

.back-link {
  display: inline-block;
  color: #e85a2a;
  text-decoration: none;
  font-size: 0.95rem;
  font-weight: 500;
}

.back-link:hover {
  text-decoration: underline;
}

.not-found {
  background: #0f1c18;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  color: #f0f5f2;
}

.not-found a {
  color: #e85a2a;
  margin-top: 20px;
}

@media (max-width: 1100px) {
  .post-number {
    right: -20px;
    font-size: 5rem;
    opacity: 0.2;
  }
}

@media (max-width: 900px) {
  .post-hero { height: 50vh; }
  .post-hero-inner { padding: 0 24px 36px; }
  .post-hero-content { max-width: 100%; }
  .post-hero-content h1 { font-size: 2.4rem; }
  .post-body { padding: 50px 24px 80px; }
  .post-container { max-width: 100%; }
  .post-number {
    position: static;
    font-size: 5rem;
    text-align: left;
    margin-bottom: 10px;
    opacity: 0.3;
  }
}
</style>