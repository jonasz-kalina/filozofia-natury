<template>
  <section class="cta">
    <div class="cta-content">
      <h2>Are you ready to take charge of your life and achieve your full potential?</h2>
      <p>
        Look no further! Sylvan is here to guide you on your journey towards personal growth, success, and fulfillment.
      </p>
      <button class="btn">Sign Up</button>
    </div>
  </section>
</template>

<style scoped>
.cta {
  background-image: url('/images/bg_hero.png');
  background-size: cover;
  background-position: center;
  background-attachment: fixed;
  color: white;
  text-align: center;
  padding: 120px 40px;
  position: relative;
}
.cta::before {
  content: '';
  position: absolute;
  inset: 0;
  background: rgba(0, 0, 0, 0.45);
}
.cta-content {
  max-width: 700px;
  margin: 0 auto;
  position: relative;
  z-index: 1;
}
.cta h2 {
  font-size: 2.8rem;
  font-weight: 500;
  line-height: 1.2;
  margin: 0 0 20px;
}
.cta p {
  font-size: 1.1rem;
  opacity: 0.85;
  margin: 0 0 30px;
}
.btn {
  padding: 14px 40px;
  background: white;
  color: #1a3a2a;
  border: none;
  border-radius: 40px;
  font-size: 1rem;
  cursor: pointer;
}
.btn:hover {
  background: #f0f0f0;
}
</style>