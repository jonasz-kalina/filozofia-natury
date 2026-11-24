<template>
  <section class="quote">
    <div class="quote-content">
      <span class="label">It's your time now</span>
      <blockquote>
        “Just as trees weather seasons, find strength in your adaptability. Let your journey be a tapestry of growth, and remember, even the darkest woods have the potential for the brightest paths.”
      </blockquote>
      <cite>— Sylvan, 2024</cite>
    </div>
  </section>
</template>

<style scoped>
.quote {
  background-image: url('/images/bg_hero.png');
  background-size: cover;
  background-position: center 30%;
  background-attachment: fixed;
  color: #dde4d7;
  text-align: center;
  padding: 160px 8vw 180px;
  position: relative;
  min-height: 70vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

.quote::before {
  content: '';
  position: absolute;
  inset: 0;
  background: rgba(10, 25, 20, 0.35);
}

.quote-content {
  max-width: 780px;
  margin: 0 auto;
  position: relative;
  z-index: 1;
}

.label {
  display: block;
  font-size: 0.85rem;
  letter-spacing: 0.08em;
  opacity: 0.75;
  margin-bottom: 18px;
  font-weight: 400;
}

blockquote {
  font-size: 2.35rem;
  font-weight: 500;
  line-height: 1.25;
  margin: 0 0 22px;
  font-style: normal;
}

cite {
  display: block;
  font-size: 0.95rem;
  font-style: normal;
  opacity: 0.8;
  letter-spacing: 0.02em;
}

@media (max-width: 768px) {
  .quote {
    padding: 100px 6vw 120px;
  }
  blockquote {
    font-size: 1.75rem;
  }
}
</style>