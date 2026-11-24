<template>
  <div>
    <!-- HERO -->
    <section class="contact-hero" ref="hero">
      <img 
        class="hero-bg" 
        src="/images/hero-contact2.jpg"
        alt=""
        :style="{ transform: `translateY(${offset}px)` }"
      />
      <div class="hero-overlay"></div>
      <div class="hero-content">
        <span class="label">KONTAKT</span>
        <h1>Dołącz do nas</h1>
        <p>Miejsca, w których cisza mówi więcej niż słowa.</p>
      </div>
    </section>

    <!-- WARSZTATY -->
    <section class="workshops">
      <div class="container">
        <div class="section-header">
          <span class="label">TERMINARZ</span>
          <h2>Najbliższe warsztaty</h2>
        </div>

        <div class="workshop-list">
          <div 
            v-for="workshop in workshops" 
            :key="workshop.id" 
            class="workshop-card"
          >
            <div class="workshop-date">
              <span class="day">{{ workshop.day }}</span>
              <span class="month">{{ workshop.month }}</span>
            </div>
            <div class="workshop-info">
              <h3>{{ workshop.title }}</h3>
              <p>{{ workshop.description }}</p>
              <div class="workshop-meta">
                <span>{{ workshop.location }}</span>
                <span>·</span>
                <span>{{ workshop.spots }}</span>
              </div>
            </div>
            <a href="#contact-form" class="workshop-btn">Zapisz się</a>
          </div>
        </div>
      </div>
    </section>

    <!-- KONTAKT -->
    <section id="contact-form" class="contact-section">
      <div class="container contact-grid">
        <div class="contact-form">
          <h2>Napisz do nas</h2>
          <form @submit.prevent="sendMessage">
            <div class="form-group">
              <label>Imię i nazwisko</label>
              <input v-model="form.name" type="text" required />
            </div>
            <div class="form-group">
              <label>E-mail</label>
              <input v-model="form.email" type="email" required />
            </div>
            <div class="form-group">
              <label>Wiadomość</label>
              <textarea v-model="form.message" rows="5" required></textarea>
            </div>
            <button type="submit" class="submit-btn">Wyślij wiadomość</button>
            <p v-if="sent" class="success">Dziękujemy! Wiadomość została wysłana.</p>
          </form>
        </div>

        <div class="contact-info">
          <h2>Kontakt</h2>
          <div class="info-item">
            <span class="info-label">E-mail</span>
            <a href="mailto:kontakt@filozofianatury.pl">kontakt@filozofianatury.pl</a>
          </div>
          <div class="info-item">
            <span class="info-label">Instagram</span>
            <a href="https://instagram.com" target="_blank">@filozofianatury</a>
          </div>
          <div class="info-item">
            <span class="info-label">Lokalizacja</span>
            <p>Lasy w okolicach Olsztyna<br>dokładne miejsce podajemy po zapisie</p>
          </div>

          <div class="phone-block">
            <span class="info-label">Telefon</span>
            <a href="tel:881236402" class="phone-number">881 236 402</a>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const hero = ref(null)
const offset = ref(0)

function updateParallax() {
  if (!hero.value) return
  const rect = hero.value.getBoundingClientRect()
  offset.value = -rect.top * 0.3
}

onMounted(() => {
  window.addEventListener('scroll', updateParallax)
  updateParallax()
})

onUnmounted(() => {
  window.removeEventListener('scroll', updateParallax)
})

const workshops = [
  {
    id: 1,
    day: '15',
    month: 'gru',
    title: 'Cisza w lesie',
    description: 'Warsztat uważności i fotografii wśród drzew. Spokojny dzień z naturą.',
    location: 'Puszcza Kampinoska',
    spots: '8 miejsc'
  },
  {
    id: 2,
    day: '12',
    month: 'sty',
    title: 'Poranny spacer z aparatem',
    description: 'Wczesna pobudka, mgła i pierwsze światło. Uczymy się widzieć las inaczej.',
    location: 'Lasy Otwockie',
    spots: '6 miejsc'
  },
  {
    id: 3,
    day: '09',
    month: 'lut',
    title: 'Ognisko i opowieści',
    description: 'Wieczorny warsztat przy ogniu. Refleksje, herbata i rozmowy.',
    location: 'Pod Warszawą',
    spots: '10 miejsc'
  }
]

const form = ref({
  name: '',
  email: '',
  message: ''
})

const sent = ref(false)

function sendMessage() {
  console.log('Wiadomość:', form.value)
  sent.value = true
  form.value = { name: '', email: '', message: '' }
}
</script>

<style scoped>
.contact-hero {
  height: 60vh;
  position: relative;
  display: flex;
  align-items: flex-end;
  overflow: hidden;
}

.hero-bg {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 120%;
  object-fit: cover;
  object-position: center top;
  will-change: transform;
}

.hero-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to bottom, rgba(0,0,0,0.2), rgba(15,28,24,0.92));
  z-index: 1;
}

.hero-content {
  position: relative;
  z-index: 2;
  padding: 0 40px 60px;
  max-width: 800px;
  margin: 0 auto;
  width: 100%;
  text-align: center;
}

.label {
  font-size: 0.65rem;
  letter-spacing: 2px;
  color: #7a9a8a;
  text-transform: uppercase;
}

.hero-content h1 {
  font-size: 4rem;
  font-weight: 500;
  color: #f0f5f2;
  margin: 8px 0 12px;
  line-height: 0.95;
}

.hero-content p {
  color: #b8d0c4;
  font-size: 1.15rem;
}

.workshops {
  background: #0f1c18;
  padding: 80px 0;
}

.container {
  max-width: 1000px;
  margin: 0 auto;
  padding: 0 40px;
}

.section-header {
  margin-bottom: 50px;
}

.section-header h2 {
  font-size: 2.8rem;
  color: #f0f5f2;
  margin: 6px 0 0;
  font-weight: 500;
}

.workshop-list {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.workshop-card {
  background: #1d382e;
  border: 1px solid #2a3a32;
  border-radius: 16px;
  padding: 28px 32px;
  display: grid;
  grid-template-columns: 90px 1fr auto;
  align-items: center;
  gap: 30px;
}

.workshop-date {
  text-align: center;
}

.workshop-date .day {
  display: block;
  font-size: 2.4rem;
  font-weight: 500;
  color: #e85a2a;
  line-height: 1;
}

.workshop-date .month {
  font-size: 0.75rem;
  letter-spacing: 1px;
  color: #7a9a8a;
  text-transform: uppercase;
}

.workshop-info h3 {
  color: #f0f5f2;
  font-size: 1.4rem;
  margin: 0 0 6px;
  font-weight: 500;
}

.workshop-info p {
  color: #8aab9a;
  margin: 0 0 8px;
  font-size: 0.95rem;
}

.workshop-meta {
  color: #7a9a8a;
  font-size: 0.85rem;
  display: flex;
  gap: 8px;
}

.workshop-btn {
  background: #e85a2a;
  color: #fff;
  text-decoration: none;
  padding: 10px 20px;
  border-radius: 20px;
  font-size: 0.85rem;
  font-weight: 500;
  white-space: nowrap;
}

.workshop-btn:hover {
  opacity: 0.9;
}

.contact-section {
  background: #0f1c18;
  padding: 40px 0 100px;
}

.contact-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 80px;
  align-items: start;
}

.contact-form h2,
.contact-info h2 {
  color: #f0f5f2;
  font-size: 2rem;
  margin-bottom: 30px;
  font-weight: 500;
}

.form-group {
  margin-bottom: 20px;
}

.form-group label {
  display: block;
  color: #8aab9a;
  font-size: 0.85rem;
  margin-bottom: 6px;
}

.form-group input,
.form-group textarea {
  width: 100%;
  background: #1d382e;
  border: 1px solid #2a3a32;
  border-radius: 8px;
  padding: 12px 16px;
  color: #f0f5f2;
  font-size: 1rem;
  box-sizing: border-box;
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: #e85a2a;
}

.submit-btn {
  background: #e85a2a;
  color: #fff;
  border: none;
  padding: 12px 28px;
  border-radius: 20px;
  font-size: 0.95rem;
  cursor: pointer;
  font-weight: 500;
}

.submit-btn:hover {
  opacity: 0.9;
}

.success {
  color: #8aab9a;
  margin-top: 16px;
}

.info-item {
  margin-bottom: 28px;
}

.info-label {
  display: block;
  color: #7a9a8a;
  font-size: 0.75rem;
  letter-spacing: 1px;
  text-transform: uppercase;
  margin-bottom: 4px;
}

.info-item a,
.info-item p {
  color: #f0f5f2;
  text-decoration: none;
  font-size: 1.1rem;
  margin: 0;
}

.info-item a:hover {
  color: #e85a2a;
}

.phone-block {
  margin-top: 36px;
}

.phone-number {
  display: block;
  font-size: 4.6rem;
  font-weight: 200;
  color: #e85a2a;
  text-decoration: none;
  letter-spacing: 1px;
  margin-top: 4px;
}

.phone-number:hover {
  opacity: 0.85;
}

@media (max-width: 800px) {
  .hero-content h1 { font-size: 2.6rem; }
  .hero-content { padding: 0 24px 40px; }
  .container { padding: 0 24px; }
  .workshop-card {
    grid-template-columns: 1fr;
    text-align: left;
    gap: 16px;
  }
  .workshop-date { text-align: left; }
  .contact-grid { grid-template-columns: 1fr; gap: 50px; }
  .phone-block { margin-top: 30px; }
  .phone-number { font-size: 3.2rem; }
}
</style>