<template>
  <section class="about-hero" ref="hero">
    <div class="about-hero-bg" :style="{ transform: `translateY(${offset}px)` }"></div>
    <div class="about-hero-overlay"></div>
    <div class="about-hero-content">
      <span class="label">(02) O NAS</span>
      <h1>Między <span>drzewami</span></h1>
      <p>Miejsce, w którym czas zwalnia.</p>
    </div>
  </section>
</template>

<script setup>
const hero = ref(null)
const offset = ref(0)

const onScroll = () => {
  if (!hero.value) return
  const rect = hero.value.getBoundingClientRect()
  offset.value = Math.max(-80, Math.min(80, rect.top * 0.2))
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
.about-hero {
  position: relative;
  height: 78vh;
  min-height: 520px;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  margin: 0 0 -20px 0;
  padding: 0;
}
.about-hero-bg {
  position: absolute;
  top: -12%;
  left: 0;
  width: 100%;
  height: 124%;
  background: url('/images/about-hero.jpg') center/cover no-repeat;
  will-change: transform;
  filter: brightness(0.45);
}
.about-hero-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to bottom, rgba(29,56,46,0.15) 0%, rgba(29,56,46,0.7) 100%);
}
.about-hero-content {
  position: relative;
  z-index: 2;
  text-align: center;
  padding: 0 20px;
}
.label {
  font-size: 0.75rem;
  letter-spacing: 2px;
  color: #7a9a8a;
  text-transform: uppercase;
}
h1 {
  font-size: 4.6rem;
  font-weight: 500;
  line-height: 0.95;
  margin: 12px 0 16px;
  color: #f0f5f2;
}
h1 span {
  font-style: italic;
  color: #e85a2a;
}
p {
  font-size: 1.2rem;
  color: #b8d0c4;
}
@media (max-width: 768px) {
  .about-hero { height: 68vh; min-height: 420px; margin-bottom: -12px; }
  h1 { font-size: 3rem; }
}
</style>