<template>
  <section id="posts" class="blog-section" ref="section">
    <div class="blog-sticky">
      <div class="blog-header">
        <span class="label">BLOG</span>
        <h2>Historie z <span>lasu</span></h2>
        <p>Refleksje, spacery i chwile, które zostają.</p>

        <div class="tabs">
          <button 
            v-for="cat in categories" 
            :key="cat.id"
            :class="{ active: activeCategory === cat.id }"
            @click="setCategory(cat.id)"
          >
            {{ cat.name }}
          </button>
        </div>
      </div>

      <div class="blog-content" :style="{ transform: `translateX(${offset}px)` }">
        <div class="blog-track">
          <div 
            v-for="(post, i) in filteredPosts" 
            :key="post.id" 
            class="blog-card"
            @click="goToPost(post.slug)"
          >
            <div class="card-bg" :style="{ backgroundImage: `url(${post.image})` }"></div>
            <div class="card-number">{{ String(i + 1).padStart(2, '0') }}</div>
            <div class="card-meta">{{ post.date }} · {{ post.category }}</div>
            <div class="card-content">
              <h3>{{ post.title }}</h3>
              <p>{{ post.excerpt }}</p>
            </div>
            <div class="card-footer">
              <span class="read-more">Czytaj dalej <span class="arrow">→</span></span>
            </div>
          </div>
        </div>
      </div>

      <div class="progress-bar">
        <span>{{ currentIndex }} / {{ filteredPosts.length }}</span>
        <div class="progress-line">
          <div class="progress-fill" :style="{ width: progressPercent + '%' }"></div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()

const categories = [
  { id: 'all', name: 'Wszystkie' },
  { id: 'reflections', name: 'Refleksje' },
  { id: 'walks', name: 'Spacery' },
  { id: 'photos', name: 'Fotografia' }
]

const posts = [
  { id: 1, slug: 'fotograficzna-podroz', title: 'Fotograficzna podróż', date: '19.06.2019', category: 'photos', excerpt: 'Witajcie, poszukiwacze piękna i chwil! Jestem Grace i z radością dzielę się z Wami moim fotograficznym światem...', image: 'https://images.pexels.com/photos/1578750/pexels-photo-1578750.jpeg?auto=compress&cs=tinysrgb&w=800' },
  { id: 2, slug: 'soczewka-na-swiat', title: 'Soczewka na świat', date: '19.06.2019', category: 'photos', excerpt: 'Hej, drodzy podróżnicy i entuzjaści fotografii! Z tej strony Grace, gotowa zabrać Was w podróż przez obiektyw...', image: 'https://images.pexels.com/photos/167699/pexels-photo-167699.jpeg?auto=compress&cs=tinysrgb&w=800' },
  { id: 3, slug: 'dzien-w-lesie', title: 'Dzień w lesie', date: '12.05.2019', category: 'walks', excerpt: 'Poranny spacer wśród drzew. Każdy krok to rozmowa z ziemią...', image: 'https://images.pexels.com/photos/1028225/pexels-photo-1028225.jpeg?auto=compress&cs=tinysrgb&w=800' },
  { id: 4, slug: 'cisza-miedzy-drzewami', title: 'Cisza między drzewami', date: '03.04.2019', category: 'reflections', excerpt: 'W lesie uczysz się słuchać tego, co nie zostało powiedziane...', image: 'https://images.pexels.com/photos/1133957/pexels-photo-1133957.jpeg?auto=compress&cs=tinysrgb&w=800' },
  { id: 5, slug: 'korzenie-i-skrzydla', title: 'Korzenie i skrzydła', date: '18.03.2019', category: 'reflections', excerpt: 'Tak jak drzewo trzyma się ziemi i sięga do nieba, tak i my...', image: 'https://images.pexels.com/photos/3408744/pexels-photo-3408744.jpeg?auto=compress&cs=tinysrgb&w=800' }
]

const activeCategory = ref('all')
const offset = ref(0)
const section = ref(null)
const currentIndex = ref(1)
const progressPercent = ref(0)

const filteredPosts = computed(() => {
  if (activeCategory.value === 'all') return posts
  return posts.filter(p => p.category === activeCategory.value)
})

const cardWidth = 420
const gap = 24

function setCategory(id) {
  activeCategory.value = id
  offset.value = 0
  currentIndex.value = 1
  progressPercent.value = 0
}

function goToPost(slug) {
  router.push(`/blog/${slug}`)
}

function onScroll() {
  if (!section.value) return
  const rect = section.value.getBoundingClientRect()
  const scrollRange = section.value.offsetHeight - window.innerHeight
  if (rect.top <= 0 && Math.abs(rect.top) < scrollRange) {
    const progress = Math.abs(rect.top) / scrollRange
    const maxOffset = (filteredPosts.value.length * (cardWidth + gap)) - window.innerWidth + 100
    offset.value = -Math.min(progress * maxOffset, maxOffset)
    progressPercent.value = progress * 100
    currentIndex.value = Math.min(Math.ceil(progress * filteredPosts.value.length) || 1, filteredPosts.value.length)
  }
}

onMounted(() => {
  window.addEventListener('scroll', onScroll, { passive: true })
  onScroll()
})

onUnmounted(() => {
  window.removeEventListener('scroll', onScroll)
})
</script>

<style scoped>
.blog-section {
  background: #1d382e;
  height: 220vh;
  position: relative;
}

.blog-sticky {
  position: sticky;
  top: 0;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  overflow: hidden;
}

.blog-header {
  padding: 0 50px 40px;
  max-width: 500px;
}

.label {
  font-size: 0.65rem;
  letter-spacing: 2px;
  color: #7a9a8a;
  text-transform: uppercase;
}

.blog-header h2 {
  font-size: 3.6rem;
  font-weight: 500;
  margin: 6px 0 12px;
  line-height: 0.95;
  color: #f0f5f2;
}

.blog-header h2 span {
  font-style: italic;
  color: #e85a2a;
}

.blog-header p {
  color: #8aab9a;
  margin-bottom: 24px;
}

.tabs {
  display: flex;
  gap: 12px;
}

.tabs button {
  background: transparent;
  border: 1px solid #3a4a42;
  color: #8aab9a;
  padding: 8px 16px;
  border-radius: 20px;
  cursor: pointer;
  font-size: 0.85rem;
}

.tabs button.active {
  background: #e85a2a;
  border-color: #e85a2a;
  color: #fff;
}

.blog-content {
  display: flex;
  will-change: transform;
  padding-left: 50px;
}

.blog-track {
  display: flex;
  gap: 24px;
}

.blog-card {
  width: 420px;
  height: 540px;
  background: #243530;
  border: 1px solid #3a4a42;
  border-radius: 22px;
  padding: 36px 32px;
  position: relative;
  flex-shrink: 0;
  display: flex;
  flex-direction: column;
  cursor: pointer;
  overflow: hidden;
}

.card-bg {
  position: absolute;
  inset: 0;
  background-size: cover;
  background-position: center;
  filter: grayscale(100%) brightness(0.35);
  opacity: 0.5;
}

.card-number {
  position: absolute;
  top: 40px;
  right: 20px;
  font-size: 7.5rem;
  font-weight: 200;
  color: #c8d5cc;
  z-index: 2;
  line-height: 0.8;
}

.card-meta {
  position: relative;
  z-index: 2;
  font-size: 0.75rem;
  color: #7a9a8a;
  letter-spacing: 0.5px;
  margin-bottom: auto;
}

.card-content {
  position: relative;
  z-index: 2;
  margin-top: auto;
}

.blog-card h3 {
  font-size: 1.8rem;
  color: #e8f0ea;
  margin: 0 0 12px;
  font-weight: 500;
}

.blog-card p {
  color: #8aab9a;
  font-size: 0.92rem;
  line-height: 1.5;
}

.card-footer {
  position: relative;
  z-index: 2;
  margin-top: 20px;
  padding-top: 16px;
  border-top: 1px solid #3a4a42;
}

.read-more {
  color: #e85a2a;
  font-size: 0.85rem;
  font-weight: 500;
}

.arrow {
  color: #fff;
}

.progress-bar {
  display: flex;
  align-items: center;
  gap: 16px;
  padding: 40px 50px 0;
  max-width: 90%;
}

.progress-bar span {
  font-size: 0.75rem;
  color: #7a9a8a;
  min-width: 50px;
}

.progress-line {
  flex: 1;
  height: 2px;
  background: #2a3a32;
  overflow: hidden;
}

.progress-fill {
  height: 100%;
  background: #e85a2a;
  transition: width 0.05s linear;
}

@media (max-width: 900px) {
  .blog-section { height: auto; }
  .blog-sticky { position: relative; height: auto; padding: 40px 0; }
  .blog-content { transform: none !important; padding-left: 20px; }
  .blog-track { overflow-x: auto; width: 100%; padding-bottom: 20px; }
  .blog-card { width: 300px; height: 460px; }
  .blog-header { padding: 0 20px 30px; }
  .blog-header h2 { font-size: 2.4rem; }
}
</style>