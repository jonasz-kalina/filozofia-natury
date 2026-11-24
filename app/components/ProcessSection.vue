<template>
  <section class="process-section" ref="section">
    <div class="process-sticky">
      <div class="process-content" :style="{ transform: `translateX(${offset}px)` }">
        <div class="process-header">
          <span class="process-label">(03) PROCESS</span>
          <h2 class="process-title">How we <span>work</span></h2>
          <p class="process-desc">A clear, proven path from first call to launch — with weekly check-ins and zero surprises.</p>
          <div class="scroll-hint">
            <span class="scroll-line"></span>
            <span>SCROLL TO EXPLORE</span>
          </div>
        </div>

        <div class="process-track">
          <div 
            v-for="(step, i) in steps" 
            :key="i" 
            class="process-card"
            :class="{ active: activeIndex === i }"
            @mouseenter="activeIndex = i"
            @mouseleave="activeIndex = null"
          >
            <div class="card-bg" :style="{ backgroundImage: `url(${step.bg})` }"></div>
            <div class="card-number">{{ String(i + 1).padStart(2, '0') }}</div>
            <div class="card-icon"><span>{{ step.icon }}</span></div>
            <div class="card-content">
              <h3>{{ step.title }}</h3>
              <p>{{ step.desc }}</p>
            </div>
            <div class="card-footer">
              <span class="card-badge">{{ step.badge }}</span>
              <span class="card-tag">{{ step.tag }}</span>
            </div>
          </div>
        </div>
      </div>

      <div class="progress-bar">
        <span class="progress-counter">{{ String(currentCard).padStart(2, '0') }} / {{ String(steps.length).padStart(2, '0') }}</span>
        <div class="progress-line">
          <div class="progress-fill" :style="{ width: progressPercent + '%' }"></div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const steps = [
  { icon: '🔍', title: 'Discover', desc: 'Workshops, interviews and research to understand your business, audience and competition.', badge: '1–2 weeks', tag: 'Workshops · Research', bg: 'https://images.pexels.com/photos/1578750/pexels-photo-1578750.jpeg?auto=compress&cs=tinysrgb&w=800' },
  { icon: '⚙️', title: 'Define', desc: 'Strategy, positioning and site architecture — a sharp brief everyone signs off on.', badge: '1–2 weeks', tag: 'Strategy · Sitemap', bg: 'https://images.pexels.com/photos/167699/pexels-photo-167699.jpeg?auto=compress&cs=tinysrgb&w=800' },
  { icon: '✏️', title: 'Design', desc: 'Concepts, design systems and interactive prototypes you can click, feel and test.', badge: '2–4 weeks', tag: 'Concepts · Prototypes', bg: 'https://images.pexels.com/photos/1028225/pexels-photo-1028225.jpeg?auto=compress&cs=tinysrgb&w=800' },
  { icon: '</>', title: 'Develop', desc: 'Clean, performant builds with motion baked in — tested on every device that matters.', badge: '3–6 weeks', tag: 'Build · QA', bg: 'https://images.pexels.com/photos/1133957/pexels-photo-1133957.jpeg?auto=compress&cs=tinysrgb&w=800' },
  { icon: '🚀', title: 'Launch & grow', desc: 'Go-live, training and handover — then we keep optimising with real data.', badge: 'Ongoing', tag: 'Launch · Optimise', bg: 'https://images.pexels.com/photos/3408744/pexels-photo-3408744.jpeg?auto=compress&cs=tinysrgb&w=800' }
]

const offset = ref(0)
const section = ref(null)
const activeIndex = ref(null)
const currentCard = ref(1)
const progressPercent = ref(0)

const cardWidth = 420
const gap = 24
const headerWidth = 460

let maxOffset = 0

function calculateMaxOffset() {
  const windowWidth = window.innerWidth
  const totalContentWidth = headerWidth + (steps.length * (cardWidth + gap))
  maxOffset = totalContentWidth - windowWidth + 100
  if (maxOffset < 0) maxOffset = 0
}

function onScroll() {
  if (!section.value) return
  
  const rect = section.value.getBoundingClientRect()
  const sectionTop = rect.top
  const sectionHeight = section.value.offsetHeight
  const windowHeight = window.innerHeight
  const scrollRange = sectionHeight - windowHeight
  
  if (sectionTop <= 0 && sectionTop > -scrollRange) {
    const progress = Math.abs(sectionTop) / scrollRange
    offset.value = -Math.min(progress * maxOffset, maxOffset)
    
    const offsetProgress = maxOffset > 0 ? Math.min(progress * maxOffset, maxOffset) / maxOffset : 0
    progressPercent.value = offsetProgress * 100
    currentCard.value = Math.min(Math.ceil(offsetProgress * steps.length) || 1, steps.length)
  } else if (sectionTop > 0) {
    offset.value = 0
    progressPercent.value = 0
    currentCard.value = 1
  }
}

onMounted(() => {
  calculateMaxOffset()
  window.addEventListener('scroll', onScroll, { passive: true })
  window.addEventListener('resize', calculateMaxOffset)
  onScroll()
})

onUnmounted(() => {
  window.removeEventListener('scroll', onScroll)
  window.removeEventListener('resize', calculateMaxOffset)
})
</script>

<style scoped>
.process-section {
  background: #1a2a24;
  height: 280vh;
  position: relative;
}

.process-sticky {
  position: sticky;
  top: 0;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  overflow: hidden;
}

.process-content {
  display: flex;
  align-items: center;
  will-change: transform;
  padding-left: 50px;
}

.process-header {
  width: 400px;
  flex-shrink: 0;
  padding-right: 50px;
}

.process-label {
  font-size: 0.65rem;
  letter-spacing: 2px;
  color: #7a9a8a;
  text-transform: uppercase;
}

.process-title {
  font-size: 3.8rem;
  font-weight: 500;
  margin: 6px 0 16px;
  line-height: 0.95;
  color: #f0f5f2;
}

.process-title span {
  font-style: italic;
  color: #e85a2a;
}

.process-desc {
  font-size: 0.9rem;
  color: #8aab9a;
  line-height: 1.55;
  margin-bottom: 24px;
}

.scroll-hint {
  display: flex;
  align-items: center;
  gap: 12px;
  font-size: 0.65rem;
  letter-spacing: 1.5px;
  color: #6a8a7a;
}

.scroll-line {
  width: 40px;
  height: 1px;
  background: #e85a2a;
}

.process-track {
  display: flex;
  gap: 24px;
}

.process-card {
  width: 420px;
  height: 560px;
  background: #243530;
  border: 1px solid #3a4a42;
  border-radius: 22px;
  padding: 36px 32px;
  position: relative;
  flex-shrink: 0;
  display: flex;
  flex-direction: column;
  cursor: pointer;
  transition: background 0.25s ease;
  overflow: hidden;
}

.card-bg {
  position: absolute;
  inset: 0;
  background-size: cover;
  background-position: center;
  filter: grayscale(100%) brightness(0.35);
  opacity: 0.45;
  pointer-events: none;
}

.process-card.active {
  background: #2d4038;
}

.process-card.active .card-bg {
  opacity: 0.6;
}

.card-number {
  position: absolute;
  top: 60px;
  right: 16px;
  font-size: 9rem;
  font-weight: 200;
  color: #c8d5cc;
  line-height: 0.8;
  pointer-events: none;
  z-index: 10;
}

.card-icon {
  width: 50px;
  height: 50px;
  border: 1px solid #e85a2a;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1rem;
  color: #e85a2a;
  position: relative;
  z-index: 2;
}

.card-content {
  margin-top: auto;
  padding-bottom: 20px;
  position: relative;
  z-index: 2;
}

.process-card h3 {
  font-size: 1.75rem;
  margin: 0 0 12px;
  font-weight: 500;
  color: #e8f0ea;
}

.process-card p {
  font-size: 0.92rem;
  color: #8aab9a;
  line-height: 1.5;
  margin: 0;
}

.card-footer {
  display: flex;
  align-items: center;
  gap: 14px;
  padding-top: 18px;
  border-top: 1px solid #3a4a42;
  position: relative;
  z-index: 2;
}

.process-card.active .card-footer {
  border-top-color: #4a5a50;
}

.card-badge {
  background: #e85a2a;
  color: #fff;
  font-size: 0.68rem;
  padding: 7px 14px;
  border-radius: 18px;
  font-weight: 500;
}

.card-tag {
  font-size: 0.78rem;
  color: #7a9a8a;
}

.progress-bar {
  display: flex;
  align-items: center;
  gap: 16px;
  padding: 0 50px;
  margin-top: 50px;
  max-width: 96%;
}

.progress-counter {
  font-size: 0.75rem;
  color: #7a9a8a;
  letter-spacing: 1px;
  min-width: 50px;
}

.progress-line {
  flex: 1;
  height: 2px;
  background: #2a3a32;
  border-radius: 1px;
  overflow: hidden;
}

.progress-fill {
  height: 100%;
  background: #e85a2a;
  transition: width 0.05s linear;
}

@media (max-width: 900px) {
  .process-section { height: auto; }
  .process-sticky { position: relative; height: auto; padding: 40px 0; }
  .process-content { flex-direction: column; align-items: flex-start; padding-left: 20px; transform: none !important; }
  .process-header { width: 100%; padding-right: 20px; margin-bottom: 24px; }
  .process-title { font-size: 2.4rem; }
  .process-track { overflow-x: auto; width: 100%; padding-bottom: 20px; }
  .process-card { width: 300px; height: 460px; }
  .card-number { font-size: 5.5rem; }
  .progress-bar { max-width: 100%; padding: 0 20px; margin-top: 20px; }
}
</style>